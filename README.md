# pc4biorobots_tutorial
From the Jupyter notebook on nanoHUB, download/build/demo the pc4biorobots GUI

* If you don't have a nanoHUB account, create one (https://nanohub.org/register/)
* Launch the tool: https://nanohub.org/tools/jupyter
* Create a new notebook with Python 3 (shown in screenshot)

![](/images/python3_nb.png)

* this creates an empty notebook with a single input "cell"

![](/images/python3_nb_cell1.png)

* Copy the following Python code and paste it into the input cell. This should download everything needed for the `pc4biorobots` app and compile the C++ code: 

```
!wget https://github.com/rheiland/pc4biorobots/archive/v1.1.zip
!unzip -o v1.1.zip
import os
os.chdir('pc4biorobots-1.1/src')
os.listdir()
!make
```

* Assuming the compilation is successful, creating the `myproj` executable, copy/paste the following into the next cell to copy `myproj` to where it belongs for the `Run` button

```
import shutil
shutil.copy('myproj','../bin')
os.chdir('..')
```

* Copy the following Python code and paste it into the next input cell.

```
style = """
    <style>
       .jupyter-widgets-output-area .output_scroll {
            height: unset !important;
            border-radius: unset !important;
            -webkit-box-shadow: unset !important;
            box-shadow: unset !important;
        }
        .jupyter-widgets-output-area  {
            height: auto !important;
            width: 100%; !important;
        }
    </style>
""" 
%matplotlib inline
from IPython.core.display import display, HTML
display(HTML(style))
import sys, os
sys.path.insert(0, os.path.abspath('bin'))
import pc4biorobots
pc4biorobots.gui
```

* this should display the GUI, let you 'Run' the model (from the `Config Basics` tab): 

![](/images/config_basics_Run.png)

* and let you interactively display results (from the `Out: Plots` tab)

![](/images/pc4biorobots_GUI.png)

