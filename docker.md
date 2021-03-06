# JUAS2022, MAD-X

During JUAS 2022, we will use Python as scripting language for the *MAD-X* course. We kindly ask you to make some "homework" before JUAS 2022 to prepare your laptop for the course.

For this course a **basic knowledge of Python is assumed**, in case you are not familiar with it an introduction to python video and a tutorial to fill the gap are provided in indico. 

During the course we will use Python3 in a Jupyter notebook and, mostly, the *numpy*, *matplotlib*, *pandas* and *cpymad* packages. 

## Jupyter-notebooks
Jupyter is a user-friendly environment to work with Python. You can find an overview [here](https://jupyter.org/).

## Working environment and Jupyter notebooks set-up
We provide the following approaches to set-up the working environment for the MAD-X course:
- Install Docker and run a Docker image we have prepared for you (to work locally in your PC).
- Install python and packges using Anaconda (to work locally in your PC).
- Use Binder (to work online on a browser).

The first two approaches allow you to work locally in your computer while the third one not. We recommend you to work locally in your PC as it will be easier to save your work and keep the tool for private use later, but the third option to work directly on a browser is also available in case you have problems with the local set-up. 

In the following we will explain how to **install locally** the required software: we propose different approaches for OSX, UNIX and Windows systems, respectively.

For **OSX** users, please follow the instructions in the *OSX: Install and run a Docker image* section.

For **UNIX** users, please follow  the instructions in the instructions in the *UNIX: Anaconda + cpymad* section.

For the **Windows** users, please follow  the instructions in the *Windows: Docker Desktop* section.

# OSX: install and run a Docker image
In order to  ease the installation procedure, we prepared a virtual environment that launch a Python3 Jupyter server (the installation on *cpymad* on OSX can be tricky, so we suggest to use the Docker image as suggested).

### STEP 1: install the Docker Desktop
Please install the [Docker Desktop](https://www.docker.com/products/docker-desktop). 

### STEP 2: run the Docker image

Once the Docker Desktop is installed and running, open a terminal and run the instruction
``` bash
>> docker run --rm -p 8888:8888 -v $PWD:/src/juas/  juastest/juas2022
```
This will download the image (~5GB): an internet connection is needed **only for the first time**, afterwords you can work offline. 
In addition, this command binds your home directory to inside the docker container such that you can save and load notebooks.
You should get something as

```bash
MACBE16107:Tutorials sterbini$ docker run -p 8888:8888 -v "$PWD":/juas sterbini/juas
[I 08:37:31.108 LabApp] Writing notebook server cookie secret to /cas/.local/share/jupyter/runtime/notebook_cookie_secret
[I 08:37:31.341 LabApp] JupyterLab extension loaded from /opt/conda/lib/python3.6/site-packages/jupyterlab
[I 08:37:31.341 LabApp] JupyterLab application directory is /opt/conda/share/jupyter/lab
[W 08:37:31.343 LabApp] JupyterLab server extension not enabled, manually loading...
[I 08:37:31.353 LabApp] JupyterLab extension loaded from /opt/conda/lib/python3.6/site-packages/jupyterlab
[I 08:37:31.353 LabApp] JupyterLab application directory is /opt/conda/share/jupyter/lab
[I 08:37:31.354 LabApp] Serving notebooks from local directory: /cas
[I 08:37:31.354 LabApp] The Jupyter Notebook is running at:
[I 08:37:31.354 LabApp] http://(4bd247dca0ba or 127.0.0.1):8888/?token=ea65f062bfce037fd7a3b47926393a0d5ded381785b0136b
[I 08:37:31.355 LabApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 08:37:31.364 LabApp] 
    
    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://127.0.0.1:8888/?token=ea65f062bfce037fd7a3b47926393a0d5ded381785b0136b
```
:::info

**The last line is the most important one**.

:::

:::info

The argument **$PWD:/src/juas/** on the command line makes the synchronization between the docker image folder and your local machine. It is important that you set-up the Docker Desktop configuration to allow it by adding the path to your Desktop on: Docker Preferences -> Resources -> File sharing. The procedure is llustrated here: <img width="1429" alt="Captura de pantalla 2021-12-15 a las 18 43 46" src="https://user-images.githubusercontent.com/72798799/146238094-7e75702d-9f87-4ad5-9d7e-5ae9d2dbf8c1.png">

:::

### STEP 3: open a jupyter-notebook from a browser

Open a web browser and connect to the python server at (**in this case**, check the last line)
http://127.0.0.1:8888/?token=ea65f062bfce037fd7a3b47926393a0d5ded381785b0136b

You have to copy and paste the last line on the address field of your browser.

You should see something like https://user-images.githubusercontent.com/72798799/146044142-2c6c33bb-427c-4326-80a2-a2642bc0833e.png but with the folders on your Desktop.

This Jupyter-notebook environment is setup with the software needed for the MAD-X tutorials.

Now you can create a new folder where to save your jupyter-notebook (right top buttom NEW) and also clic on *NEW-> Python 3 Notebook* on the right top icon (https://user-images.githubusercontent.com/72798799/146044142-2c6c33bb-427c-4326-80a2-a2642bc0833e.png) and test the code example at the end of this document to verify that everything is working as expected.

# UNIX: Anaconda distribution

For UNIX system the simplest way to install Python environment on your laptop is to setup manually your environment by installing [*anaconda*](http://docs.continuum.io/_downloads/9ee215ff15fde24bf01791d719084950/Anaconda-Starter-Guide.pdf) from  
http://docs.continuum.io/anaconda/ (go to the bottom of the web page).

### STEP 1: Anaconda installation
We suggest to install the Python 3.9 version (latest)
https://www.anaconda.com/distribution/. 

List the packages that are installed with
```
>> conda list
```
and verify that you have *matplotlib*, *numpy*, *scipy*, *pandas*, *sympy*.
If some of them are missing, please install them with, e.g.,
```
>> conda install -c conda-forge matplotlib 
```

### STEP 2: *cpymad* installation
The standard *anaconda* distribution comes with most of the needed packages but *cpymad*. You can install it following the instructions from https://github.com/hibtc/cpymad. In most of the case it is enough to open a terminal and do
```
>> pip install cpymad --only-binary cpymad
```

### STEP 3: Jupyter
Now you can launch from a terminal Jupyter
```
>> jupyter-notebook
```

:::info
If Jupyter-notebook is not installed in your system you can install it with 
```
>> conda install -c conda-forge notebook
```
:::

The *jupyter-notebook* command will open a browser.

You can clic on the NEW->Python 3 Notebook icon on the top right (https://user-images.githubusercontent.com/72798799/146044142-2c6c33bb-427c-4326-80a2-a2642bc0833e.png) and test the code example at the end of this document to verify that everything is working as expected.

# Windows: Docker Desktop

### STEP 1: install
If you have **Windows 10 Home, Professional or Enterprise** you can follow **the instructions given for OSX** and install the Docker Desktop from [here](https://docs.docker.com/desktop/windows/install/) .

:::info

In order to have Docker running properly the virtualization needs to be activated. If you have problems running Docker due to this problem please follow the steps explained here: https://mashtips.com/enable-virtualization-windows-10/.

:::

### STEP 2:launch the docker image

Now open the Docker Quickstart (icon on the Desktop). It will take some time to start the virtual machine. Then open a Command Prompt window using the cmd program and move to your home folder typing

```bash
>> cd
```
Then type

```bash
>> docker run -p 8888:8888 -v %cd%:/src/juas/  juastest/juas2022
```
This download the docker image (only for the first time, ~5 GB) and run it.

You will get something like (https://user-images.githubusercontent.com/72798799/146367178-20318779-e336-4de1-870e-61562f2d16c3.png)

:::info

**The last line is the most important one**.

:::

### STEP 3: open Jupyter from a browser

Open a web browser and connect to the python server at (**in this case**, see the last line of the previous screenshot)
http://127.0.0.1:8888/?token=HereGoesYourAlphanumericToken


It will open a browser and you should get something like 
![](https://user-images.githubusercontent.com/72798799/146044142-2c6c33bb-427c-4326-80a2-a2642bc0833e.png)

You can clic on the NEW->Python 3 Notebook icon on the top right (https://user-images.githubusercontent.com/72798799/146044142-2c6c33bb-427c-4326-80a2-a2642bc0833e.png) and test the code example at the end of this document to verify that everything is working as expected.

# Problems with the set-up.

If you have problems with the set-up you can contact us by email and we will be happy to help (nuria.fuster@ific.uv.es).

Otherwise you can work during the MAD-X tutorial directly on a browser through binder (https://mybinder.org/). We will provide you with the links to the jupyter-notebooks but special attention has to be paid using this approach to save the progress by downloading the jupyter-notebooks at the end of the workshop or your progress will be lost. 

You can try here https://mybinder.org/v2/gh/fusterma/MADX_JUAS2022/HEAD?filepath=test.ipynb

You can clic on the NEW->Python 3 Notebook icon on the top right (https://user-images.githubusercontent.com/72798799/146044142-2c6c33bb-427c-4326-80a2-a2642bc0833e.png) and test the code example at the end of this document to verify that everything is working as expected.

# An example of Python3 notebook.
Open a new Python3 jupyter notebook: NEW->Python 3 Notebook and copy and paste the following lines on the jupyter-notebook boxes and give it a try!

You can import the python library of MAD-X (*cpymad*) with the following command.
```python
from cpymad.madx import Madx
from matplotlib import pyplot as plt
myMad = Madx()
```

and now you can twiss a simple FODO cell (more details during the course) with the following code
``` python
myString='''
! *********************************************************************
! Second part
! *********************************************************************

! *********************************************************************
! Definition of parameters
! *********************************************************************

l_cell=100;
quadrupoleLenght=5;
f=200;
myK:=1/f/quadrupoleLenght;// m^-2

! *********************************************************************
! Definition of magnet
! ********************************************************************* 
QF: quadrupole, L=quadrupoleLenght, K1:=myK;
QD: quadrupole, L=quadrupoleLenght, K1:=-myK;

! *********************************************************************
! Definition of sequence
! *********************************************************************
myCell:sequence, refer=entry, L=L_CELL;
quadrupole1: QF, at=0;
marker1: marker, at=25;
quadrupole2: QD, at=50;
endsequence;

! *********************************************************************
! Definition of beam
! *********************************************************************
beam, particle=proton, energy=2;

! *********************************************************************
! Use of the sequence
! *********************************************************************
use, sequence=myCell;

! *********************************************************************
! TWISS
! *********************************************************************
title, 'My first twiss';
twiss, file=myFirstTwiss.twiss;
'''
myMad.input(myString);
```
You can see the *Q1* and *betymax* parameters by executing this cell
``` python
myString='''
value, table(SUMM,Q1);
value, table(SUMM,betymax);
'''
myMad.input(myString);
```
and you can get a pandas dataframe with the information of the lattice by
``` python
myDF=myMad.table.twiss.dframe()
myDF[['name','s','betx','bety']].head()
```
You should get something like
![](https://codimd.web.cern.ch/uploads/upload_6ffb4ff57ec6f11c385e9a405604b1c3.png)

To plot some data of the *twiss* table you can execute
``` python
plt.plot(myDF['s'],myDF['betx'],'ob-')
plt.plot(myDF['s'],myDF['bety'],'or-')
plt.legend()
plt.grid()
plt.xlabel('s [m]')
plt.ylabel('[m]')
plt.title('My first FODO cell')
```
![](https://codimd.web.cern.ch/uploads/upload_468cfab86d69ef405edce079a68b399f.png)

You can do also a bit of symbolic computation with 

``` python
import sympy as sy
import numpy as np
from sympy import init_session
init_session() 
la=np.linalg
L_cell=sy.Symbol('L_cell', positive=True);
f_1=sy.Symbol('f_1', positive=True);
f_2=sy.Symbol('f_2', positive=True);
f=sy.Symbol('f', positive=True);

QF=sy.Matrix([[1,0], [-1/f,1]])
DRIFT=sy.Matrix([[1,L_cell/2], [0,1]])
QD=sy.Matrix([[1,0], [1/f,1]])
# This is the OTM 
M=DRIFT@QD@DRIFT@QF
M=sy.simplify(M)
M

```

An example of test ipython notebook is shown in

https://cernbox.cern.ch/index.php/s/JJCu7KRPAjuitVF

You will learn much more at JUAS 2022. **See you (remotely)  there!**





