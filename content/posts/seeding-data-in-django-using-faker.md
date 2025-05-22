---
author: ["Chris Achinga"]
title: "Seeding Data in Django Using Faker"
date: "2024-03-27"
description: "Seeding data in a Django project can be essential for development and testing."
tags: ["data", "django"]
ShowToc: true
---

Seeding data in a Django project can be essential for development and testing. Faker, a Python library, provides a convenient way to generate placeholder data realistically.
This guide will explore how to seed data using Faker in Django.


Here is an example model:

First, let’s consider an example model consisting of `Skill` and `Category`.

```python 
from django.db import models
import uuid

class Skill(models.Model):
    id = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False, unique=True)
    title = models.CharField(max_length=200, unique=True)

    def __str__(self):
        return self.title

class Category(models.Model):
    id = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False, unique=True)
    title = models.CharField(max_length=200, unique=True)

    def __str__(self):
        return self.title
```

## Creating a Seeder Command

To seed data easily, we’ll create a custom management command.

1. Create a directory `management/commands` inside your app.
2. Create a file `seed_data.py` inside the commands directory.
3. 
Here’s the content of `seed_data.py`:

```python
from django.core.management.base import BaseCommand
from app.models import Skill, Category
from faker import Faker
import random

class Command(BaseCommand):
    help = "Seed database with sample data for app.models"

    def add_arguments(self, parser):
        parser.add_argument("num_skills", type=int, help="Number of skills to create")
        parser.add_argument("num_categories", type=int, help="Number of categories to create")

    def handle(self, *args, **kwargs):
        num_skills = kwargs["num_skills"]
        num_categories = kwargs["num_categories"]

        self.stdout.write(self.style.SUCCESS("Seeding database..."))

        fake = Faker()

        # Create sample skills
        existing_skill_titles = set(Skill.objects.values_list("title", flat=True))
        for _ in range(num_skills):
            skill_title = fake.word()
            while skill_title in existing_skill_titles:
                skill_title = fake.word()
            Skill.objects.create(title=skill_title)
            existing_skill_titles.add(skill_title)

        # Create sample categories
        existing_category_titles = set(Category.objects.values_list("title", flat=True))
        for _ in range(num_categories):
            category_title = fake.word()
            while category_title in existing_category_titles:
                category_title = fake.word()
            Category.objects.create(title=category_title)
            existing_category_titles.add(category_title)

        self.stdout.write(self.style.SUCCESS("Database seeding completed."))
```

## Running the Seeder

Activate the seeder by running the following command:

```shell
python manage.py seed_data <num_skills> <num_categories>
```

Replace `<num_skills>` and `<num_categories>` with the desired number of skills and categories to create.

Example:

```shell
python manage.py seed_data 10 5
```

This command will seed the database with 10 skills and 5 categories.
Seeding data with Faker in Django can greatly streamline your development process by populating your database with realistic placeholder data.

Resources:

https://medium.com/django-unleashed/seeding-data-in-django-using-faker-b9355bbbbb74

