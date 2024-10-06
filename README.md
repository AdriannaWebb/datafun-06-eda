# datafun-06-eda

## Create datafu-06-eda 
- create the repo in github 
- cloned to machine in Documents folder
- opened folder in vs code

## Create git ignore 
create a file named .gitignore with the following commands 
```
# This .gitignore file lists content that does NOT need to be tracked in the project history

# Python virtual environment
.venv/

# Visual Studio Code settings and workspace
.vscode/

# Compiled Python files
__pycache__/

# macOS system files
.DS_Store

# Editor backup files
*~

# Python Jupyter Notebook checkpoints and runtime files
.ipynb_checkpoints/
*.ipynb_meta/
```

## Commit changes 

In the terminal, ``` run git add ``` . then ```git commit -m "cloned and gitignore"```, then ```git push -u origin main``` to add / commit / push to GitHub.


## Create a virtual enviornment 


Use your terminal to create your project virtual environment by running venv as a Python module (py -m venv) and providing a name to use for the local folder as .venv.
If you name it differently, be sure that your folder name is included in the .gitignore file. 

Windows command

```shell
py -m venv .venv
```

Mac/Linux command

```
python3 -m venv .venv
```

You should get a new folder in your project repository named .venv. 
If VS Code asks to use use this environment, click Yes. 

### 5. Activate the Project Virtual Environment (Every time you open a terminal) 

Use your terminal to activate your project virtual environment. (Do this every time you open a new terminal to work on your project.)

Windows commands to activate your .venv. Try the first. Use the second if the first doesn't work. 

```shell
.venv\Scripts\Activate
.\.venv\Scripts\Activate.ps1
```

Mac/Linux command to activate your .venv

```shell
source .venv/bin/activate
```
Verify you see the virtual environment name (.venv) in your terminal prompt.

## Install Requirements 


If you like, you can use a [requirements.txt](requirements.txt) file to install dependencies instead.
These files are helpful in projects when we have several external packages to install and it can be good practice.

To do so, you'll need a file named requirements.txt in the root folder of your repository listing each external package used, one per line. 

```
jupyterlab
pandas
pyarrow
matplotlib
seaborn
```

If using Windows PowerShell, install into your active project virtual environment with this command:

```shell
py -m pip install -r requirements.txt
```

If using Mac or Linux, install into your active project virtual environment with this command:

```shell
python3 -m pip install -r requirements.txt
```

If successful, you will now be able to use the following line in your Python scripts.
If you get an error on this line, work through the steps above to
create, activate, and install into your local project virtual environment,
and make sure VS Code is using your .venv local project environment. 

```
import requests
```

## Select Data
I will be using the seaborn dataset called healthexp.csv
and example can be found here: https://github.com/mwaskom/seaborn-data/blob/master/healthexp.csv 

## Create Jupyter Notebook

1. Create the Notebook: In the VS Code Explorer, create a new file i.e., yourname_eda.ipynb. Ensure it has a .ipynb extension.
2. Verify your new notebook is open for editing. If needed, view the project files in VS Code Explorer and double-click the notebook file to open it for editing.
3. Add a Markdown cell at the top of your notebook with the introduction (include the title, author, date and the purpose of the project).

## Import Dependencies at the top

```
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import pyarrow as pa 

```

## Data Acquisition
```
# Load the dataset into a pandas DataFrame 
df = sns.load_dataset('healthexp')

# Inspect first rows of the DataFrame
print(df.head())
```

## Perform Inital Inspections 
```
print(df.head(10))
print(df.shape)
print(df.dtypes)
```
## Initial Descriptive Statistics
``` 
print(df.describe())
```

## Initial Data Distributions

**Numerical Columns:**
```
# Inspect histograms for all numerical columns
df.hist()

# Show all plots
plt.show()
```
**Categorical Columns:***
```
# Inspect value counts by categorical column
df['Country'].value_counts()

# Inspect value counts for all categorical columns
for col in df.select_dtypes(include=['object', 'category']).columns:
    # Display count plot
    sns.countplot(x=col, data=df)
    plt.title(f'Distribution of {col}')
    plt.show()

# Show all plots
plt.show()
```

 