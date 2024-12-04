# BlogStation

# Requirements
- Install python and pip
```bash
sudo apt update
sudo apt install python3 python3-pip
```
- Install `venv` Module
```bash
sudo apt install python3-venv
```

# Project setup
- Create project root directory `BlogStation` and change directory to it
```bash
mkdir BlogStation
cd BlogStation
```
- Set Up a Virtual Environment `env` and activate it
```bash
python3 -m venv env
source env/bin/activate
```
- Install Django to the virtual environment and Save installed packages to a `requirements.txt` file
```bash
pip install django
pip freeze > requirements.txt
```
- Start our Django Project `BlogStation` to the current directory
```bash
django-admin startproject BlogStation .
```
- Setup `.gitignore` file
```bash
touch .gitignore
```
- Initialize git repository
```bash
git init
git add . && git commit -m "Initial commit"
```