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



## set up on vm
### SSH to VM
    gcloud compute ssh --project=PROJECT_ID --zone=ZONE jupyter-server
### update OS
    sudo apt-get update
### install pip ( package manager python )
    sudo apt install python3-pip

### install jupyter on vm
    pip install jupyter
### Run jupyter on vm
    jupyter notebook
