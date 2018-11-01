# Getting Setup on Paperspace

Get public ip for ml-in-a box

### Setup jupyter and common packages

`ssh paperspace@PUBLIC_IP`
 

On the server:

```
sudo apt install tmux htop zsh tree vim
```

```
pip install kaggle  # to download data using kaggles API
pip install notebook --upgrade
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
then generate certs
```
openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mykey.key -out mycert.pem
```
You can just hit [enter] through all the questions.

```
sudo ufw allow 8888
jupyter notebook --generate-config
```
[Based off this](https://by-the-water.github.io/posts/2017/05/16/setting-up-a-jupyter-notebook-server-on-paperspace.html)
After this, ipython should work on the server and you should see `mykey.key` and `mycert.pem` if you type `ls`.




### Accessing Jupyter
Paste the following into `~/.jupyter/jupyter_notebook_config.py`
```
c.NotebookApp.certfile = u'/home/paperspace/mycert.pem'
c.NotebookApp.keyfile = u'/home/paperspace/mykey.key'
# Set ip to '*' to bind on all interfaces (ips) for the public server
c.NotebookApp.ip = '*'
# c.NotebookApp.password = u''
c.NotebookApp.allow_origin = '*'
c.NotebookApp.allow_remote_access = True
c.NotebookApp.open_browser = False
```

Then, run tmux and jupyter notebook
```
export PATH="$HOME/anaconda3/bin:$PATH"
jupyter notebook
```

your nb server should be at https://{PUBLIC_IP}:8888/tree?#running

(you will have to click advanced/proceed to access it).


    

### FAQ

I cannot access https://{PUBLIC_IP}:8888

- make sure URL is right and you are in chrome
- see if there are useful error messages from the terminal
- note that the token  is different from your machine password. It is outputted from the terminal.
- contact me, I can try to debug
    

wrong version of python/cannot find `jupyter command`:
```
export PATH="$HOME/anaconda3/bin:$PATH"
```


How do I enable jupyter extensions?
```
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install --user
jupyter nbextension enable codefolding/main
```

How do I copy files from my local machine?
```
scp  [localpath] paperspace@184.105.174.55:./
```


Which paperspace instance type am I using?
P5000 ML-in-a-box
