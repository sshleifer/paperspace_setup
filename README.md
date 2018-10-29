# Getting Setup on paperspace

email sshleifer@gmail.com
I will give you a public IP and password over some secure means of communication

then

`ssh paperspace@PUBLIC_IP`
 

On the server:

```
sudo apt install tmux htop zsh tree vim
pip install kaggle  # to download data using kaggles API
pip install notebook --upgrade
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mykey.key -out mycert.pem
sudo ufw allow 8888
```
[Based off this](https://by-the-water.github.io/posts/2017/05/16/setting-up-a-jupyter-notebook-server-on-paperspace.html)

After this, ipython should work on the server.


### Accessing Jupyter
Paste the following into `~/.jupyter/jupyter_notebook_config.py`
```
c.NotebookApp.certfile = u'/home/paperspace/cert/mycert.pem'
c.NotebookApp.keyfile = u'/home/paperspace/cert/mykey.key'
# Set ip to '*' to bind on all interfaces (ips) for the public server
c.NotebookApp.ip = '*'
c.NotebookApp.password = u''
c.NotebookApp.allow_origin = '*'
c.NotebookApp.allow_remote_access = True
c.NotebookApp.open_browser = False
```

your nb server should be at https://{PUBLIC_IP}:8888/tree?#running


### Tips
How to copy files from your local machine
```
scp  [localpath] paperspace@184.105.174.55:./
```


### FAQ

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
