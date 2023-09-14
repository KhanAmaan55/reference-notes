# Python virtual environment in linux

If you're a Python developer, you know how important it is to keep your projects organised and avoid package conflicts. That's where virtual environments come in. These isolated copies of Python allow you to work on a specific project without affecting others, by creating a separate "playground" with its own packages and dependencies. In this blog post, we'll explain what virtual environments are, why you might want to use them, and how to create and manage them in your own projects. Whether you're a beginner or an experienced Python developer, virtual environments are a valuable tool to have in your toolkit.

### What is Virtual Environment
Virtual environments are like separate "playgrounds" for your Python projects. They let you work on a specific project without affecting others, so you can avoid package conflicts and keep your projects organised. By creating a virtual environment, you get an isolated copy of Python that you can use for that project alone, with its own packages and dependencies

### Virtual Environment in LINUX

1. Install pip:
```bash
sudo apt-get install python-pip
```
2. Install virtualenv:
```bash
pip install virtualenv
```
3. Check version:
```bash
virtualenv --version
```
4. Create virtualenv:
```bash
virtualenv virtualenv_name
```
5. Create virtualenv with specific python version:
```bash
virtualenv -p /usr/bin/python3 virtualenv_name
virtualenv -p /usr/bin/python2.7 virtualenv_name
```
6. Activate virtualenv:
```bash
source virtualenv_name/bin/activate
```
7. Deactivate virtualenv:
```bash
deactivate
```
## Requirement.txt file

When working with virtual environments in Python, it's crucial to manage your project's dependencies carefully. Installing packages directly into your virtual environment can be messy, as it can be hard to keep track of which packages you've installed and their respective versions. That's where a requirements.txt file comes in handy. By listing all your project's dependencies in a single file, you can easily recreate your environment on another machine or share it with other developers. This helps ensure that everyone working on your project has the same dependencies installed, making it easier to collaborate and avoiding any surprises or conflicts down the line.
These commands generate a requirements.txt file for your Python project.

If you're using Python 3, the command is:
```bash
pip3 freeze > requirements.txt
```
If you're using Python 2, the command is:
```bash
pip freeze > requirements.txt
```
The command pip freeze lists all the packages installed in your virtual environment, along with their versions. The '>' operator redirects this output to a file named requirements.txt, which will be saved in the current directory.

This file can then be shared with other developers or used to recreate your virtual environment on another machine by running
```bash
pip install -r requirements.txt.
```
