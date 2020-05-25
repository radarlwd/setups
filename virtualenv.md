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
# [Manage Multiple Projects, Virtual Enviroments, and Environment Variables](https://www.youtube.com/watch?v=cY2NXB_Tqq0&t=621s)
1. Create a directory.
```
mkdir my_proj
cd my_proj
```
2. Create an enviroment with conda
```
conda create --name my_project_env pkg1 pkg2
```
3. In the environment directory, activate the environment.
```
source activate my_proj_env
```
- Deactivate the environment.
```
source deactivate my_proj_env
```
4. Export the environment to a file
```
conda env export > environment.yaml
```
5. Replcate the environment stored in environment.yaml
```
conda env create -f environment.yaml
```
- List all environment on the machine
```
conda env list
```
6. Set environment variables.
In my_proj_env:
```
mkdir -p etc/conda/activate.d
mkdir -p etc/conda/deactivate.d
touch etc/conda/activate.d/env_var.sh
touch etc/conda/deactivate.d/env_vars.sh
```
In ```activate/env_vars.sh````, paste the following
```
#!/bin/sh
export DATABASE_URI="postgresql://user:pass@db_server:5432/test_db"
```
In ```deactivate/env_vars.sh```, paste the following
```
#!/bin/sh
unset DATABASE_URI
```
7. To check deactivate the activate the environment
```
conda deactivate
conda activate my_proj_env
echo $DATABASE_URI
```

8. Place the environment.yaml in the project folder.

# Auto activate the virtual environment if exitsts.
9. Add the following to ```~/.bash_profile```
```
#Modified from: 
#https://github.com/chdoig/conda-auto-env

#Auto activate conda environments
function conda_auto_env() {
  if [ -e "environment.yaml" ]; then
    ENV_NAME=$(head -n 1 environment.yaml | cut -f2 -d ' ')
    # Check if you are already in the environment
    if [[ $CONDA_PREFIX != *$ENV_NAME* ]]; then
      # Try to activate environment
      conda activate $ENV_NAME &>/dev/null
    fi
  fi
}

export PROMPT_COMMAND="conda_auto_env;$PROMPT_COMMAND"

```
