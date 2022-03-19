
# Data Science Work-Flow

## 2019.01.08 Ivan Gadjev

---

My workflow with VSCode, anaconda, jupyter, and cookiecutter:

1. Open Anaconda
    - NB: If PC was asleep or restarted a running Anaconda may be unresponsive to "launch" commands. I think this is an issue for my system only. :/
2. Choose the virtual environment to activate (data_sci_base, ivan-main, etc.)
    - The cookiecutter package should be installed, if you want to handle project mangement and file structure with cookiecutter data science.
3. Launch VS Code
    - This will start a new window of VSC with the  activated venv. The venv can be changed inside VSC by `Ctrl+Shift+P > python select interpreter > select venv`
4. Launch jupyter notebook from inside VSC. Open a terminal and enter `jupyter notebook`. This takes care of the server and kernel connection problems that PyCharm was having with jupyter.

---

## cookiecutter

Cookiecutter is a python module that handles project structure.

Please read these:

[Cookiecutter Data Science](https://drivendata.github.io/cookiecutter-data-science/#why-use-this-project-structure)

[Cookiecutter Data Science - atom and jupyter](https://medium.com/@rrfd/cookiecutter-data-science-organize-your-projects-atom-and-jupyter-2be7862f487e)

Installing `cookiecutter` for a venv using anaconda.
1. In anaconda navigator, add the channel `conda-forge`
    -Channels > Add > type "conda-forge" > Update Channels
    -I think this is needed for extra packages like `cookiecutter` to be available.
2. `cookiecutter` will now be available for the venv in the navigator or by using pip install

Using `cookiecutter`
1. At a terminal with the venv activated and at the project path enter:
    ```
    D:\my\science\projects>cookiecutter 'url-to-git-of-project-structure'
    ```
    - The Data Science project structure is located here:
    ```
    D:\my\science\projects>cookiecutter https://github.com/drivendata/cookiecutter-data-science
    ```
2. Enter the required fields. If a field is left blank the default value is filled in.

src folder

The `.\src` folder as a module. This folder has a `__init__.py` file that allows it to contain custom function and class definitions that can be imported by projects that use the file structure. To add the `.\src` forlder as a module, the directory must be added to the path of the venv interpreter. This can be handled by `pip install --editable path\to\project\src` run at a terminal with venv. For example:

```bash
(data_sci_base) D:\Dropbox\py_projects>pip install --editable D:\Dropbox\py_projects\kaggle_LAX\lax_inout
Obtaining file:///D:/Dropbox/py_projects/kaggle_LAX/lax_inout
Installing collected packages: src
  Found existing installation: src 0.1.0
    Uninstalling src-0.1.0:
      Successfully uninstalled src-0.1.0
  Running setup.py develop for src
Successfully installed src

(data_sci_base) D:\Dropbox\py_projects>
```

Once this is done, custom functions can be written in the file structure:

```
.\src\
    + customFuncs
        - foo.py
        - otherClasses.py
    - __init__.py
```

Inside `foo.py`, define methods as functions:

```python
def fooFunc1(arg1):
    return arg1 + 1
def nextFunc(...):
    ...
    return ...
```

import custom classes as follows:

```python
from src.customFuncs import foo.py

print(foo.fooFunc1(9))
```
