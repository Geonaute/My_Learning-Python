# Anaconda

## Installation
### M-1: Windows
* https://www.anaconda.com/
* tick the checkbox corresponding to "Add to path". This will enable using `conda` in the terminal.
> NOTE: In some cases, we might have to install Anaconda on Linux using WSL. Because, there are errors like Microsoft Visual C++ 14.0 related to some packages.

### M-2: Ubuntu (WSL)
* Download Anaconda (`.sh` file) for Linux from this [website](https://www.anaconda.com/distribution/#download-section)
* `$ ./Anaconda3-2019.03-Linux-x86_64.sh`
  ```console
  Welcome to Anaconda3 2019.03

  In order to continue the installation process, please review the license
  agreement.
  Please, press ENTER to continue
  >>>
  ===================================
  Anaconda End User License Agreement
  ===================================
  ```

* Directory location: Home directory `cd ~`
  ```console
  Anaconda3 will now be installed into this location:
  /home/abhijit/anaconda3

    - Press ENTER to confirm the location
    - Press CTRL-C to abort the installation
    - Or specify a different location below

  [/home/abhijit/anaconda3] >>>
  PREFIX=/home/abhijit/anaconda3
  ```

## Shortcuts
* Open Jupyter notebook using `$ jupyter notebook` on terminal (win 10) in a preferable directory.
  E.g.:
  - goto "F:\Coding\jupyter-notebook"
  - open cmd here
  - type `jupyter notebook` on terminal.
* All the packages installed using conda present in this directory - `"F:\Softwares\Anaconda3\Lib\site-packages"`
* Various environments created inside conda are present in this directory - `"F:\Softwares\Anaconda3\envs"`
* JUPYTER NOTEBOOK shortcut keys - 
  https://www.dataquest.io/blog/jupyter-notebook-tips-tricks-shortcuts/
* <kbd>D + D</kbd> - to delete cell
* <kbd>A</kbd> - add a cell above selected cell
* <kbd>B</kbd> - add a cell below selected cell
* <kbd>M</kbd> - cell as **Markdown**.
* <kbd>shift + enter</kbd> - to run the cell and goto the next cell below.
* To import `beautifulsoup` package, use this - `import bs4`, NOT this - ~`import beautifulsoup4`~

## Conda
* `conda list` - shows the list of packages installed
* `conda list --revisions` - shows the revisions of the installation since first installation.
  ```
  2019-01-30 17:14:43  (rev 4)
     beautifulsoup4  {4.6.0 -> 4.7.1}
    +soupsieve-1.7.1

  2019-02-07 20:57:34  (rev 5)
     ca-certificates  {2018.12.5 -> 2019.1.23}
     conda  {4.6.1 -> 4.6.2}
     pandas  {0.20.3 -> 0.24.1}

  2019-02-08 19:26:01  (rev 6)
     pandas  {0.24.1 -> 0.20.3}
  ```
* ##### `conda install pandas=0.20.3` - install a specific version of a package
* #### install/uninstall packages using internet with a proxy 
  Follow this steps: <br/>
  - `> conda config` - would create a file: `.condarc` in directory - "C:\Users\abhijit"
  - write the snippet following [YAML](http://www.yamllint.com/) syntax
  ```yaml
  # Proxy settings: http://[username]:[password]@[server]:[port]
  proxy_servers:
  http: http://abhijit:CL00102@192.9.200.22:8080
  https: http://abhijit:CL00102@192.9.200.22:8080
  ```
* ##### `conda info -e`: List all Environments inside Anaconda(Installaed): 

* ##### `conda create -n <yourenvname> python=<x.x> anaconda`: Create a Virtual Environment (similar to the base environment). 
  > NOTE: It's better not to install the entire Anaconda in an environment. Instead, install the packages which are needed. 
* ##### `conda activate <yourenvname>`: Activate virtual environment. Do this before installing packages.
  ```console
  C:\Users\abhijit>conda activate kiwienv

  (kiwienv) C:\Users\abhijit>
  ```
* ##### `deactivate`: Deactivate virtual environment. Do this within the activated environment.
  ```console
  (kiwienv) C:\Users\abhijit>conda deactivate

  C:\Users\abhijit>
  ```
* ##### `conda install -n <yourenvname> [package]`: Install package(s) in virtual environment.
* ##### `conda remove -n yourenvname -all`: Delete a no longer needed virtual environment.
* ##### Change directory (F:\Coding\Github_repos\Kiwi) in __Anaconda Prompt__:
  ```console
  (base) C:\Users\abhijit>F:

  (base) F:\>cd Coding\Github_repos\Kiwi

  (base) F:\Coding\Github_repos\Kiwi>
  ```
* SSL Error:
  ```console
  Solving environment: failed

  CondaHTTPError: HTTP 000 CONNECTION FAILED for url <https://repo.anaconda.com/pkgs/r/noarch/repodata.json.bz2>
  Elapsed: -

  An HTTP error occurred when trying to retrieve this URL.
  HTTP errors are often intermittent, and a simple retry will get you on your way.

  If your current network has https://www.anaconda.com blocked, please file
  a support request with your network engineering team.

  SSLError(MaxRetryError('HTTPSConnectionPool(host=\'repo.anaconda.com\', port=443): Max retries exceeded with url: /pkgs/r/noarch/repodata.json.bz2 (Caused by SSLError(SSLError("bad handshake: Error([(\'SSL routines\', \'tls_process_server_certificate\', \'certificate verify failed\')])")))'))
  ```
  
  __Solution:__<br/>
  Do this on Anaconda prompt - `conda config --set ssl_verify no`
  > Warning: Note that this opens you up to some pretty serious attacks.
* #### error: Microsoft Visual C++ 14.0 is required
  ```console
      error: Microsoft Visual C++ 14.0 is required. Get it with "Microsoft Visual C++ Build Tools": https://visualstudio.microsoft.com/downloads/

      ----------------------------------------
  ```
  This error is found while installing `mysqlclient` package using `pip`.
  __Solution:__ <br/>
  - Download the package from the website for system's specs (Python version, 32-bit or 64-bit)
  ```console
  C:\Users\abhijit>python
  Python 3.7.1 (default, Dec 10 2018, 22:54:23) [MSC v.1915 64 bit (AMD64)] :: Anaconda, Inc. on win32
  Type "help", "copyright", "credits" or "license" for more information.
  >>>
  ```
  - Search "python libraries uci" in Google.
  - Click the 1st link - https://www.lfd.uci.edu/~gohlke/pythonlibs/
  - <kbd>ctrl + f</kbd> for `mysqlclient`
  - Download the package file for your system.
  - Now, install the package in required Anaconda Environment using `pip`
  ```console
  (kiwienv) C:\Users\abhijit\Desktop>pip install mysqlclient-1.4.2-cp36-cp36m-win_amd64.whl
  Processing c:\users\abhijit\desktop\mysqlclient-1.4.2-cp36-cp36m-win_amd64.whl
  Installing collected packages: mysqlclient
  Successfully installed mysqlclient-1.4.2
  ```
  
## Packages
#### NOTE: all packages here are not installed by default
* **Html2Text** 
  - M-1: https://anaconda.org/akode/html2text [NOT Successful]
  - M-2: Install using `pip` in conda environment
    + On Windows, open "Anaconda Prompt"
    + `> pip install html2text`
    + Now, check if `html2text` package is installed: try `conda list` on same/separate terminal.
    + DONE!
* **PLotly** - https://anaconda.org/plotly/plotly
* **conda-env**
  - conda env export lists all conda and pip packages in an environment. `conda-env` must be installed in the conda root (`conda install -c conda conda-env`).
