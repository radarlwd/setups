# [virtualenv - A way to separate diffrent python enviroments for different projects](https://www.youtube.com/watch?v=N5vscPTWKOk&t=2s)
1. Install virtualenv
```
pip install virtualenv
```
- List all packages
```
pip list
```
2. Make a directory for the enviroment
```
mkdir enviroments
cd !$
```
3. Create the virtual enviroment
```
virtualenv proj_env
```
4. Activate the environment. The prompt of the environment will be shown.
```
source proj_env/bin/activate
```
5. Export the local dependencies to the requirements.txt.
```
pip freeze --local > requirements.txt
cat requirements.txt
```
- To get out of the local environment
```
deactivate
```
- To remove the enviroment
```
rm -rf proj_env/
```
Create a virtual environment with a specified package
```
virtualenv -p /usr/bin/pythonx.x new_proj_env
source new_proj_env/bin/activate
```
To install all requirements stored in a file.
```
pip install -r requirements.txt
```


