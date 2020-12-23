---
layout: post
title: Setting up a robust computing machine
#subtitle:
bigimg: /img/2018-62-11-img1.jpeg
tags: [python, tools, basic, jupyter, tmux]
comments: true
css: /css/jupyter.css
---

**Preamble**: This post is largely based from the python set-up document kindly prepared by [John Livingston](https://github.com/john-livingston) for our group at UTokyo.

# 1. Introduction
Programming skill is almost a must to learn nowadays. Python has become a popular choice for both beginners and advanced programmers because it has a relatively simple (reader-friendly) syntax and has a large community support.

Now I will guide you through the basics of setting up a robust and convenient platform-independent Python environment, which includes:

- Python using `miniconda`
as a programming environment manager;
- `Jupyter notebook`/ `lab`
as editor for developing and sharing code;
- `Git` and `Github` 
for version control.

If you haven't tried python, I recommend learning it interactively via [codecademy](https://www.codecademy.com/learn/python). If you like to learn from video examples, try this [Youtube Tutorial](https://www.youtube.com/user/sentdex/playlists).

# 2. Python Setup
We will use miniconda, a lightweight, command line-only version of the powerful Python distribution Anaconda. First, download the Python 3.x version of the miniconda installer for your platform from [here](http://conda.pydata.org/miniconda.html). I do not recommend using Windows for scientific computing, so if you have a PC, consider installing one of the many user-friendly flavors of Linux (e.g. [Mint](https://www.linuxmint.com/download.php)), either natively/dual-boot or in a [virtual machine](https://www.virtualbox.org/wiki/Downloads).

If you have no choice but to use Python in Windows, try this [guide](http://conda.pydata.org/docs/download.html) instead.

The following instructions are for **Linux** machine. 

## 2.1. Installing Miniconda
Open a new terminal (or `CTRL+ALT+T`) and go to the directory of your downloaded miniconda.

```shell
$ cd ~/Downloads/Miniconda[x]-latest-Linux-[x].sh
```
where [x] is the version of your choice.

Make the file executable:

```sh
$ chmod +x Miniconda[x]-latest-Linux-[x].sh
```
and then install:

```shell
$ ./Miniconda[x]-latest-Linux-[x].sh
```

Note that `$` symbolizes the shell prompt.

## 2.2. Creating your first Python environment


We will create an environment called `py3` with Python 3.x installed. As of writing, Python 3.6 is the most recent version.

```shell
$ conda create -n py3 python=3.6
```

Then, activate to enter into the `py3` environment: 

```shell
$ source activate py3
```

Note: If you installed Miniconda on Windows, you can enter the environment using `activate py3` 
i.e. without typing the `source` command.

Note that the handler of your terminal changes to:

```shell
(py3) $
```
where the name inside the brackets indicate the environment you are currently using.


To see what is installed within the `py3` environment:

```shell
(py3) $ conda list
```
The output is:

```shell
openssl:	1.0.2h-1     
pip:		8.1.2-py27_0 
python:	3.6.1-0     
readline:	6.2-2        
setuptools:	23.0.0-py27_0
sqlite:		3.13.0-0     
tk:		8.5.18-0     
wheel:		0.29.0-py27_0
zlib:		1.2.8-3
```

These libraries are needed to make python 3.6 work. Other libraries in this list, such as `pip`, are used for installing other libraries/tools.

Now, get out the py3 environment:

```shell
(py3) $ source deactivate
$ 
```

## 2.3 Creating More than One Environment

If you want to create a new environment called `py2` and install an older version of python in it,

```shell
$ conda create -n py2 python=2.7
$ source activate py2
(py2) $
```
Quickly see if it has `python 2.7` installed and then deactivate.

```shell
(py2) $ python --version
Python 2.7.11 :: Continuum Analytics, Inc.
$ source deactivate 
```

Great. Now, if you want to see the list of environments you have created,

```shell
$ conda env list
root		*home/usrname/miniconda
py3		home/usrname/miniconda/envs/py3
py2		home/usrname/miniconda/envs/py2
```

If you want to remove `py2` environment (because you already have the recent python 3.6),

```shell
$ conda remove env -n py2 --all
```

To see the difference between Python 2.x and 3.x, see [this link](http://sebastianraschka.com/Articles/2014_python_2_3_key_diff.html). For a conda cheatsheet, please refer to [this document](http://conda.pydata.org/docs/_downloads/conda-cheatsheet.pdf).

You see, the conda environment functions like a folder where a copy of certain programs/scripts are located. So if you want to run a code using python 3 for example, it will only use the programs within that environment (i.e. py3). If you break something, it will only affect whatever is inside this environment. You can have another environment (i.e. py2) with totally different version and it won't affect other environment. Note that without this environment partition capability provided by conda, it would be difficult to have python 2 and 3 working together because they require different dependencies.

## 2.4. Installing Libraries Within the Environment

Now we will install additional **libraries** (e.g. numpy, matplotlib, pandas) and **programs** (e.g. jupyter, git) *within* py3 environment.

Using `conda`, install [`numpy`](http://www.numpy.org/)--for numerical computations, and [matplotlib](http://matplotlib.org/)--for plotting capabilities. It is also recommended, but optional, to install [scipy](https://www.scipy.org/) and [pandas](http://pandas.pydata.org/) for more advanced capabilities relevant to scientific computing. 
<!---
Using pip, install [`astroml`](http://www.astroml.org/)--a Machine Learning Astronomy package for python.
--->

```shell
$ source activate py3
(py3) $ conda install numpy matplotlib scipy pandas
```

If you cannot find a specific library you need say `seaborn`, you can also install using `pip`.

```shell
(py3) $ pip install seaborn
```

`pip` will install the specified packages including all its dependencies.


Note: Make sure you install the library using `conda/pip` *inside* the intended environment. Otherwise, the libraries will be installed in your `root` directory.

Now, launch `ipython` (ipython is the interactive version of python):

```ipython
(py3) $ ipython
```

You have successfully installed ipython if you see your terminal becomes like this:

```ipython
In [1] : 
```

To check the version of your python:

```ipython
In [1] : !python --version
Python 3.6.1 :: Continuum Analytics, Inc.
```

You can check that the numpy, matplotlib, etc. works correctly if it shows no error.

```ipython
In [2]:  import numpy, matplotlib, scipy, pandas
In [3]:
```

To get out of the ipython:

```ipython
In [3] : exit()
```

And you will see you're back to:

```ipython
(py3) $ 
```

# 3. Jupyter Notebook

We will view and edit codes using [Jupyter](http://jupyter.org/). Jupyter is perfect if you want to learn about Python, particular Python packages, or even about entire subjects, there exist an [enormous number of freely available documents](https://github.com/jupyter/jupyter/wiki/A-gallery-of-interesting-Jupyter-Notebooks), called `Jupyter Notebooks`. There are some which contain good introduction to Python, some which contain advanced tutorials about complex data analysis methods and tools, and some which are actually entire books on a particular subject. In all cases, Jupyter Notebooks are interactive – you follow the code and run it for yourself. This is a game changer for reproducible research which is now becoming population in the astronomy community. 

```shell
(py3) $ conda install jupyter
```
Then, launch jupyter notebook:

```shell
(py3) $ jupyter notebook
```

You will then see your favorite browser will open a new tab (if you're currently using one). This browser tab is connected to a running Python kernel in the background, so you can actually run the code you see, modify it, etc. This is what makes Jupyter Notebooks so powerful. To understand how to use Jupyter Notebooks, there are plenty of online documentation like [for scientific computing](http://nbviewer.jupyter.org/github/jrjohansson/scientific-python-lectures/blob/master/Lecture-0-Scientific-Computing-with-Python.ipynb). You can download a [sample notebook](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Running%20Code.ipynb) by clicking the down arrow in the upper right corner.

Go to the directory where it is saved and open it using jupyter notebook:

```shell
(py3) $ cd ~/Downloads/
(py3) ~/Downloads $ jupyter notebook Lecture-0-Scientific-Computing-with-Python.ipynb
```

A new tab of the web browser will pop up. Now you can read the document and run some of the parts that contain a code. Those cells are marked with ipython marker `In [1]`. Click this cell and press `SHIFT+ENTER` and you will see an output `Out [1]`. 

To close this, click `FILE` and `SAVE & EXIT`. If you close the tab, the notebook will still be running.  So close it by entering `CTRL+C` in the open terminal. Generally, you cannot use the terminal where the Jupyter kernel is running.

### Update:

A recent update on Jupyter notebook turned-into-an-IDE (GUI-based) is called [Jupyter lab](https://github.com/jupyterlab/jupyterlab). If you like having more GUI in the notebook, so go ahead and check Jupyter lab with more description in this [blog](http://blog.jupyter.org/2016/07/14/jupyter-lab-alpha/). 
Also, google [colaboratory](https://colab.research.google.com) provides jupyter environment running in the cloud. One useful feature of colab is being able to run the notebook from github by replacing `github.com` with `colab.research.google.com/github/`. For example, `https://github.com/jpdeleon/Group_Exer/blob/master/Group%20Exercises.ipynb` --> `colab.research.google.com/github/jpdeleon/Group_Exer/blob/master/Group%20Exercises.ipynb`.

You can install jupyter lab, as simple as before

```shell
(py3) $ conda install jupyterlab
```
Then, launch jupyter lab:

```shell
(py3) $ jupyter lab
```

### Working with jupyter notebook remotely
See [working with remote jupyter](https://jpdeleon.github.io/2018-02-10-remote-jupyter/).

# 4. Git and GitHub
[git](https://git-scm.com) is a version management tool and [github](https://github.com) is a complementary online repository.

For software development, I abhor seeing my old codes which look like

```
script.py
script2.py
script_revised.c
script_revised2.c
```

To solve this difficulty of tracking the version of my files, I introduce [git](https://git-scm.com/). Now let us install git.

```shell
(py3) $ conda install git
```

Take the time to learn how to use git– it will change your life. The documentation is here, and there are plenty of other great online resources to help you, including tutorials with [terminal emulators](https://try.github.io/levels/1/challenges/1) running right in the browser to help get you started.


## 4.1 Creating your (new) github repository
Suppose you have a fresh github account, create a new repository by clicking the green `New repository` button in your home page.

Give it a name, say `sample`, and check the box `Initialize this repository with a README` before clicking the `Create repository` button.

Now, get a local copy of the `sample` to your machine by clicking `Clone or download` and `Copy to clipboard`.

Open a new terminal, and clone:

```shell
$ git clone git@github.com:jpdeleon/sample.git
$ cd sample/
```

You should see that it currently contains a README file only. Now, add a new jupyter notebook or any file inside the `sample` folder.

```shell
$ git status
```

It will show the new files you added (in red). You should add them so that git can begin tracking them. For example you added `new_noteboook.ipynb`, so

```shell
$ git add new_notebook
```

If you edit the notebook or any other files, git will record such changes. If you're already satisfied, you can create a check point for your project by

```shell
$ git commit -am "this can be any comment"
```

Before you can save your files to a github repo, you have to provide set up your ssh keys:

Go to you github profile, click `Settings` in the upper right hand corner and then `SSH and GPG keys`. Click the green `New SSH key` button and fill the name of your machine/latop.


Check if you have created ssh keys already

```shell
$ less ~/.ssh/id_rsa.pub
```

If you haven't created one yet, try

```shell
$ ssh-keygen
<ENTER>
...
<ENTER>
$ less ~/.ssh/id_rsa.pub
```

Copy your keys and paste it to the github page earlier. If done correctly, 

```shell
$ ssh -T git@github.com
```

will show explicitly say you've successfully authenticated the ssh keys.

Finally, we can save our `sample` project to github by

```shell
$ git push origin master 
```
Now refresh your project page in github and you should see that `new_notebook.ipynb` and other new files have just been added.

## Other useful tools

* ssh
* tmux
```
$ ssh_pc
$ tmux new -s [session-name]
CTRL+b then d
$ tmux a -t [session-name]
$ exit
```
* nano/gedit
To add syntax highlighting, configure [nanorc](https://github.com/scopatz/nanorc).
* atom
* .bashrc

From my exprience in working with Linux, `.bashrc` is invaluable.
I normally create a separate file named `.alias` which is sourced in my `.bashrc` file. `.alias` is basically a list of useful shortcuts and tricks to make my work flow smooth and efficient. For example, 
```bash
alias ntbk='jupyter notebook'
alias ssh_pc='ssh usrname@ipaddress'
```

### We're done!
Now you have successfully set-up your machine. You can check out the [notebook gallery](https://github.com/ipython/ipython/wiki/A-gallery-of-interesting-IPython-Notebooks) to learn the basics and quickly learn adavanced applications.

Enjoy learning!
