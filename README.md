# paperspace_setup
paperspace_setup

```
sudo apt install tmux htop zsh tree vim
pip install kaggle
pip install pydicom
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install --user
jupyter nbextension enable codefolding/main
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

```
[helpful](https://by-the-water.github.io/posts/2017/05/16/setting-up-a-jupyter-notebook-server-on-paperspace.html)

### notebook access

```
c.NotebookApp.certfile = u'/home/paperspace/cert/mycert.pem'
c.NotebookApp.keyfile = u'/home/paperspace/cert/mykey.key'
# Set ip to '*' to bind on all interfaces (ips) for the public server
c.NotebookApp.ip = '*'
c.NotebookApp.password = u''
c.NotebookApp.allow_origin = '*'
c.NotebookApp.allow_remote_access = True
c.NotebookApp.open_browser = False

# It is a good idea to set a known, fixed port for server access
c.NotebookApp.port = 8888
```

### How to copy files from your local machine

```
scp  [localpath] paperspace@184.105.174.55:./
```
