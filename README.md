#### Running VScode locally while connecting to Zaphod jupyter kernel 


```bash
# Using `zaphod` alias in ~/.ssh/config 
ssh zaphod
screen -R persistent_jupyter_server

# setup desired environment for jupyter server
# e.g. conda activate <ENV_NAME>

mkdir jupyter_servers_workdir

# start jupyter server
jupyter notebook \
--notebook-dir=$HOME/jupyter_servers_workdir \
--no-browser \  # stop browser opening on startup
--port=8888 # leave as default

```
Should receive URL like `http://localhost:8888/?token=5f11a3 ...`
