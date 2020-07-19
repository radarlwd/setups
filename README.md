# setups

https://docs.python-guide.org/dev/virtualenvs/


packages management tool comparision
https://medium.com/python-pandemonium/better-python-dependency-and-package-management-b5d8ea29dff1



https://stackoverflow.com/questions/31684375/automatically-create-requirements-txt

You can use the following code to generate a requirements.txt file:
```
pip install pipreqs
```
```
pipreqs /path/to/project
more info related to pipreqs can be found here.
```

Sometimes you come across pip freeze, but this saves all packages in the environment including those that you don't use in your current project.
