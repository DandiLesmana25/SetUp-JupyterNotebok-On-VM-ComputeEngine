# SetUp-JupyterNotebok-On-ComputeEngine
## Create Vm instance
| Name | jupyter-server |
| --- | --- |
| Region | us-central1 |
| Zone | us-central1-a |
| Machine series | N1 |
| Machine type | n1-standard-1 |
| Boot disk | Ubuntu 20.04 LTS |
| Size boot disk | 20 GB |
| Firewall | Allow HTTP traffic & Allow HTTPS traffic 
| Network-tag | allow-ports-jupyter-8888

## Create Firewall rule
| Name | firewall-allow-port-8888 |
| --- | --- |
| Target tags | allow-ports-jupyter-8888 |
| Source Ip range | 0.0.0.0/0 |
| Protocol and ports | TCP: 8888



## set up jupyter on vm
### SSH to VM
    gcloud compute ssh --project=PROJECT_ID --zone=ZONE jupyter-server
### update OS
    sudo apt-get update
### install pip ( package manager python )
    sudo apt install python3-pip
### install jupyter on vm
    pip install jupyter
### generate a jupyter notebook configuration file 
    jupyter notebook --generate-config
#### output
    /home/dandiserver/.jupyter/jupyter_notebook_config.py
### edit config file
     nano /home/dandiserver/.jupyter/jupyter_notebook_config.py
### you can simply copy and paste these lines at the beginning of the configuration file
    c.NotebookApp.token = ''
    c.NotebookApp.ip = '*'
    c.NotebookApp.open_browser = False
    c.NotebookApp.port = 8888
### SAVE => control + x to exit and press Y to save changes then press enter.
### Run jupyter on vm
    jupyter notebook

### open a new browser and enter your IP address and port number as it is
    http://34.122.224.36:8888
## Done

# Run Jupiter Notebook as a service
Saat Kita close SSH, proses notebook akan berhenti. Jika Kita ingin proses ini dijalankan terus-menerus di virtual mesin, Kita perlu mengonversi proses ini ke Linux service.
### Step 1: Tambahkan file baru dengan nama "jupyter.service" di "/etc/systemd/system/"
    nano /etc/systemd/system/jupyter.service
