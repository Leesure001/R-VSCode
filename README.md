# R-VSCode

This is a brife [tutorial](https://leesure001.github.io/R-VSCode/) about using R in VSCode through SSH server.

## <span style="color: blue;">Introduction</span>

This article provides a tutorial about using R in VS Code through SSH server, the processes are normally the same when you use R in your local computer.

## <span style="color: blue;">Install Visual Studio Code</span>

Use the official [Visual Studio Code](https://code.visualstudio.com/) website to download and install Visual Studio Code matching your local computer system.

## <span style="color: blue;">Connect to SSH Server</span>

Add SSH host in Visual Studio Code using this extensions

* Open command palette

* Search for `Remote-SSH: Add New SSH Host...`

* Type your command how you connect to the server

* Select the SSH config file: you can use the default one, listing on the top `/Users/user.name/.ssh/config`

* Now you can connect to your remote server successfully

* Next time when you want to connect it, you can click the icon on the bottom left corner, select the host you want to connect, then you will connect to it easily

## <span style="color: blue;">Install R</span>

Use the official [R](https://cloud.r-project.org/) website to download and install R matching your server system.

## <span style="color: blue;">Install Python</span>

Use the official [Python](https://www.python.org/) website to download and install Python matching your server system.

## <span style="color: blue;">Install Extensions</span>

Install the extensions in the following picture in Visual Studio Code

![**Install extensions: Python, Pylance, R, R Debugger**](Extensions.png)

**Note: If you are trying to use R in Visual Studio Code through SSH servre, please install all the above, including R, Python and extensions, and the following R packages, Python package, in your SSH server environemnt.**

## <span style="color: blue;">Install Required R package</span>

Open R environment in the terminal in your Visual Studio Code. If you don't know the R version in your computer, just type `R` then click `TAB` on your keyboard twice, it will return the R version in your system, if it returns `R-4.1.2`, then type `R-4.1.2` in the terminal, you will enter a R environment.
```r
install.packages("languageserver")
packageVersion("languageserver")
install.packages("rmarkdown")
packageVersion("rmarkdown")
install.packages("httpgd")
packageVersion("httpgd")
```
Enable `r.plot.useHttpgd` in Visual Studio Code settings: Open Visual Studio Code setting, copy `r.plot.useHttpgd` to the search bar, then check the box.

## <span style="color: blue;">Install Radian</span>

[Radian](https://github.com/randy3k/radian) is highly recommended as the R terminal for interactive use. It requires Python which should be available on most Linux distributions out of the box.
To install it globally:
```r
pip install -U radian
```
or
```r
pip3 install -U radian
```
Or if you don't have root privilege, you may want to install it only for yourself:
```r
pip install --user radian
```
or
```r
pip3 install --user radian
```
Enable `r.bracketedPaste` in Visual Studio Code settings: Open Visual Studio Code setting, copy `r.bracketedPaste` to the search bar, then check the box.

## <span style="color: blue;">Environment Setting</span>

Type the following commands in the termial: Suppose your R version in your environemnt is R-4.1.2
```r
which R-4.1.2
which radian
```
This will return the paths for **R** and **radian**. Suppose your **R** path is `/home/user/.local/bin/R-4.1.2`, **radian** path is `/home/user/.local/bin/radian`, then

* Search `r.rterm.linux` in Visual Studio Code setting, type your **radian** path here, such as `/home/user/.local/bin/radian`

* Search `r.rpath.linux` in Visual Studio Code setting, type your **R** path here, such as `/home/user/.local/bin/R-4.1.2`

* Search `r.rterm.option` in Visual Studio Code setting, click `Add Item`, type `--r-binary=/home/user/.local/bin/R-4.1.2`, then save the change, remember change the **R** path to the **R** path in your own environment.

**Reminder: There may be three choices when you search above three things in Visual Studio Code setting, `User`, `Remote`, `Workspace`, if you are using R in Visual Studio Code through SSH server, select `Remote`, if you are using R in Visual Studio Code in your local computer, select `User`, then modify `r.rterm.linux` and `r.rpath.linux` matching your local computer system.**

## <span style="color: blue;">Other Option</span>

You can also use the following code to install anaconda and use it to create a R environment, then following all the processes above.
```r 
wget https://repo.anaconda.com/archive/Anaconda3-2022.10-Linux-x86_64.sh
bash Anaconda3-2022.10-Linux-x86_64.sh
conda --version
conda create -n my-r-env r-base
conda activate my-r-env
R --version
R
q()
conda deactivate
```

If you want to enter `bash` automatically when you create a new terminal, you can search `terminal.integrated.defaultProfile.linux`, then select `bash`.

## <span style="color: blue;">Reference</span>

[R Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=reditorsupport.r)

[Installation wiki pages](https://github.com/REditorSupport/vscode-R)