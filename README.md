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
Should receive URL like `http://localhost:${SERVER_PORT_NUMBER}/?token=5f11a3 ...`
where `SERVER_PORT_NUMBER` is `8888` in this case. 

Exit `screen` instance using `Ctrl+A+D`.  
`[detached from 486658.persistent_jupyter_server]` 

> Note: to reattach later, use `screen -x persistent_jupyter_server`

Return to local machine with `exit`. 
`Connection to 129.... closed.`

```bash
ssh -N -f -L $LOCAL_PORT_NUMBER:localhost:$SERVER_PORT_NUMBER $HOSTNAME

# i.e.
ssh -N -f -L 8888:localhost:8888 zaphod
```

Then, open VScode (locally) and open notebook.  Connect to kernel and paste in URL 
(replacing `SERVER_PORT_NUMBER` with `LOCAL_PORT_NUMBER`)

Confirm connection with: 
```python
>>> import multiprocessing as mp 
>>> mp.cpu_count()
64
```
