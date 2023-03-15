# Lab Report

### **Name:** *Vihar Shah*

### **ID:** *202001110*

### **Lab:** *05*

### **Objective:** *Static analysis of random github repositories using Static Analysis Tools*

---

## Repository Analysed
> For the Purpose of this lab, the repository selected to test various tools is *https://github.com/TheAlgorithms/Python*

The selected repository contains following various folders.
![image](https://user-images.githubusercontent.com/123557378/225272622-bbe8783f-e36a-4985-94c8-06cfcd176bef.png)

To make the comparison between the tools easier, all the tools are used to analysis a single sub-folder, viz., **backtracking** from the repository

## MYPY

*MYPY* is static type checker tool for python. It helps ensure that the variables and functions used in the code work correctly. It analyzes the code to check for type errors as well which can occur during run time without actually running the code!

> following command can be used to install mypy
~~~bash
pip install mypy
~~~

> to check a file and generate a report, we run following command
~~~bash
python -m mypy <python filename(s) / foldername(s)>
~~~

It generates a report indicating any errors that it detected.

### Analyzing The Repository

We perform analysis on one of the sub-folders of the selected repository, **ciphers** which has following contents.  
![image](https://user-images.githubusercontent.com/123557378/225272788-3d770698-04cf-431a-a76c-1a92b655fac9.png)

> We check the file **all_combinations.py** by running the following command
~~~bash
python -m mypy all_combinations.py
~~~
![image](https://user-images.githubusercontent.com/123557378/225279251-8227cb2c-79f7-495d-84a8-3a5946559c68.png)

The above output shows no error occured during the analysis of the file  

> To check the entire current directory at once, we can run following command
~~~bash
python -m mypy .
~~~

> The corresponding output obtained is as follows:

![image](https://user-images.githubusercontent.com/123557378/225279409-28f660d2-b22e-4fb7-90ae-4476177788ad.png)
 
 We can see that **MYPY** was not able to find any errors in the selected sub-folder.
 
 ---
 
 ## PYLINT
 
 *PYLINT* is another static code analyzer tool used to enforce coding standards, check for errors, and make code refactoring suggestions.  
 Pylint can perform a more thorough analysis of the code compared to other linters but it also makes it slow compared to them.  
 It is highly configurable and option to be configurable by the user as per his/her needs.
 
 > Pylint can be installed on the system by running following command
~~~bash
pip install pylint
~~~

> to run pylint on a file, following syntax can be followed
~~~bash
python -m pylint <python filename(s)/foldername(s)>
~~~
 
 ### Analyzing The Repository

> We check the same file by running the following command
~~~bash
python -m pylint all_combinations.py
~~~

> The resulting output is generated as follows:

![image](https://user-images.githubusercontent.com/123557378/225275256-0af1dbe4-eff9-4ed6-8bd2-63384f0df5a9.png)

Unlike, *MYPY*, *PYLINT* found many errors. However all the errors found focus on variable naming and documentation of the code.  
- Issues like the camel-case naming convention and docstrings to indicate what the function does are absent.
    - Although not a source for run-time errors, these problems can be troublesome if some new developer wants to or has to work on the project as (s)he can have tough time identifying the program flow.
- The issue of redefining the outer scope variable can be troublesome and can lead to some unexpected working of the code or misunderstanding in the program flow by someone reading the code for the first time.

> To check the entire current directory at once, we can run following command
~~~bash
python -m pylint *.py
~~~
> Note that pylint only checks python files so **\*.py** indicates that we are passing all the files with .py extention.

> The corresponding output obtained is as follows:

![image](https://user-images.githubusercontent.com/123557378/225282027-f81aaa33-1728-464c-aec9-80627686c08e.png)

Unlike, *MYPY*, *PYLINT* generated a long list of such errors from various python files of which many were worth rectifying.  


 ---
 
 ## PYFLAKES
 
 *Pyflakes* is faster alternative to *pylint* mainly because it only examines the syntax tree of each file individuallly by parsing them instead of importing them.
 
 > pyflakes can be installed by running following command
 ~~~bash
 pip install pyflakes
 ~~~
 
 > to peform pyflakes check on a file, one can start by running
 ~~~bash
 python -m pyflakes <python filename(s)/foldername(s)>
 ~~~
 
 ### Analyzing The Repository
 
 > To perform the analysis on **all_combinations.py** file, following command is used

 ~~~bash
 python -m pyflakes all_combinations.py
 ~~~
 
 > The resulting output is as follows:
 
![image](https://user-images.githubusercontent.com/123557378/225286385-4592e941-bf1d-4235-a44b-61b43d886724.png)

> Just like for *all_combinations.py*, *pyflakes* does not generate any output for the entire **backtracking** folder.
> The output generated by *pyflakes* for the entire selected repository can be seen as follows

![image](https://user-images.githubusercontent.com/123557378/225286936-2f58f4be-6768-4dc9-bff5-b69ddce1ed33.png)

The *pyflakes* errors all point to unused import statements and variable declarations. This can be very helpful in performing code cleaning on a large project and to prevent using unnecessary memory.

This indicates an entirely different usage scenario compared to the previously used tools, viz., *mypy* and *pyflint* indicating that it is better to perform analysis using various tools to get a better idea at the types of errors present instead of sticking to just one tool.


 ---
 
 ## PYCODESTYLE
 
 *Pycodestyle* is simple style convention checker. It checks the code styling against some standard PEP8 conventions.  
 Addditional style definitions as per user choice can also be defined alongside other plugins.
 
 > To install pycodestyle, run the following command

~~~bash
pip install pycodestyle
~~~
 
 > static analysis on a file using pycodestyle can be performed as follows

~~~bash
python -m pycodestyle <python filename/foldername>
 
 ### Analyzing The Repository
 
 > checking the file **all_combinations.py**
 ~~~bash
 python -m pycodestyle all_combinations.py
 ~~~
 
 > The output obtained is as follows:

 ![image](https://user-images.githubusercontent.com/123557378/225289731-34d47372-578e-4aec-80c6-8695be542cce.png)


> Checking the folder,
~~~bash
python -m pycodestyle .
~~~

> The output obtained is 

![image](https://user-images.githubusercontent.com/123557378/225290076-8a0f0f16-1ec8-4322-af1a-e60b115fc53b.png)

The errors obtained here are mainly extra long code written in a single line.
