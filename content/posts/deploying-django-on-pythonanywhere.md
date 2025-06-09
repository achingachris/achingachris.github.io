---
author: ["Chris Achinga"]
title: "Deploying A Django Project on PythonAnywhere"
date: "2023-05-23"
description: "This article provides a comprehensive, step-by-step guide to help you deploy your existing Django project on PythonAnywhere successfully."
tags: ["python", "deployment", "django"]
ShowToc: true
---


Deploying a Django project on [PythonAnywhere](https://pythonanywhere.com/) lets you make your web application accessible online. With PythonAnywhere, you can create a web app, configure it with a WSGI file, and host your Django project seamlessly.


## Prerequisites:

* [Pythonanywhere](http://pythonanywhere.com) Account

* An existing Django project is ready for deployment.

* GitHub (Code Repo)

* Basic Familiarity with Django and the command line interface


For demo purposes, please refer to the following project: It’s a voting app from the official [Django Tutorial](https://docs.djangoproject.com/en/4.2/intro/tutorial01/)

https://github.com/achingachris/Django-Polls-Tutorials

## Uploading Your Code to pythonanywhere

Open a console(terminal) on your pythonanywhere dashboard:

![](/images/past/pa-1.png)

Just click on the blue bash button to open a terminal-like page:

![](/images/past/pa-2.png)

If your Django project is hosted on a code-sharing platform like GitHub or Bitbucket, you can clone it directly onto PythonAnywhere using a Bash console. Here's an example command:

```bash
git clone https://github.com/achingachris/Django-Polls-Tutorials.git
```

![](/images/past/pa-3.png)

Alternatively, as mentioned in the [documentation](https://help.pythonanywhere.com/pages/FileBrowser/), you can explore other methods of uploading and downloading files on PythonAnywhere.

## Set Up a Virtual Environment and Install Dependencies

Create a virtual environment in the Bash console on PythonAnywhere and install Django and any other project dependencies.

To do so, use the command:

```bash
 mkvirtualenv --python=/usr/bin/python3.10 <environment name>
```

Replace `<environment name>` with any name, you want to give to your virtual environment.

So for the demo, I will use:

```bash
mkvirtualenv --python=/usr/bin/python3.10 polls
```

![](/images/past/pa-4.png)

To install the dependencies, change the active directive on your console to the folder cloned from GitHub(or uploaded):

```bash
cd projectname
```

Ensure you have the `requirements.txt` file


To install the dependencies, run:

```bash
pip install -r requirements.txt
```

## Configure the Web App and WSGI File

To set up your Django project on PythonAnywhere, follow these steps:

**Create a Web app with Manual Configuration:**

Navigate to the "Web Apps" tab on PythonAnywhere and create a new web app.

Select the default domain for free accounts

Choose the "Manual Configuration" option and select the appropriate Python version matching your virtual environment.


Choose a Python version: (preferably v3.10)


You will get notified that you have to set up the configuration manually:


**Specify the Virtual Environment:**

Scroll down to the "virtualenv" section of the web app configuration, and enter the name of your virtual environment (e.g., polls).


**Edit the WSGI File:**

Scroll down to the “Code” section of the web app configuration.

Click the link and make the necessary changes to the WSGI file. You will be redirected to an in-browser text editor view:


Delete everything except the Django section and then uncomment that section. Your WSGI file should look something like this:

```python
# +++++++++++ DJANGO +++++++++++
    # To use your own Django app use code like this:
    import os
    import sys
    
    # assuming your Django settings file is at '/home/myusername/mysite/mysite/settings.py'
    path = '/home/myusername/mysite'
    if path not in sys.path:
        sys.path.insert(0, path)
    
    os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'
    
    ## Uncomment the lines below depending on your Django version
    ###### then, for Django >=1.5:
    from django.core.wsgi import get_wsgi_application
    application = get_wsgi_application()
    ###### or, for older Django <=1.4
    #import django.core.handlers.wsgi
    #application = django.core.handlers.wsgi.WSGIHandler()
```

Edit the code to configure your Django application. For the demo, the project name is `polls` , and my username is `chrisachinga`:

```python

import os
import sys
    

path = '/home/chrisachinga/polls'
   if path not in sys.path:
      sys.path.insert(0, path)
    
os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'

from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()
```


Remember to save after editing the file.

**Database Setup**

We will use the simple SQLite database for this demo, so no extra configuration is needed.

Go to the **Consoles tab**, start a bash console, and use `cd` to navigate to the directory where your Django projects [`manage.py`](http://manage.py) lives, then run:

```bash
 ./manage.py migrate
```



You can now check if everything is okay. Click the link on the web tab to view the deployed version: *“*[*chrisachinga.pythonanywhere.com*](http://chrisachinga.pythonanywhere.com)*”*


On loading the site, it’s most likely to get this error: `DisallowedHost`:


Here's how you can solve it:

Open the Django settings file (`settings.py`) in your project. Locate the `**ALLOWED_HOSTS**` variable. It should be a list or tuple.

Add `'`[`chrisachinga.pythonanywhere.com`](http://chrisachinga.pythonanywhere.com)`'` to the list of allowed hosts. Example:

```python
ALLOWED_HOSTS = ['localhost', '127.0.0.1', 'chrisachinga.pythonanywhere.com']
```

I edited mine on GitHub:


Note: Include any other domains or IP addresses you want to allow access to your site.

To update the code on pythonanywhere, you can pull the code from the terminal:

```bash
git fetch
git pull
```

After that, head back to the web application tab and reload the site:


And now, when I load the site on: IT WORKS!



**Next Steps:**

You can interact with the Django shell and API on the console to create a superuser, migrate databases, and more. Just ensure the virtualenv is turned on.

## **Conclusion:**

Following this step-by-step guide, you can successfully deploy your Django project on PythonAnywhere. Remember to adapt the instructions to match your project's specific configuration and requirements. PythonAnywhere offers a convenient platform for hosting your Django application, allowing you to share your web app with users across the internet. Enjoy the benefits of a live Django site hosted on PythonAnywhere and provide an exceptional user experience.