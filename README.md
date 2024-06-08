# SetUp-JupyterNotebok-On-ComputeEngine
| Name | web-server |
| --- | --- |
| Region | asia-southeast2 |
| Zone | asia-southeast2-b |
| Machine series | N1 |
| Machine type | n1-standard-1 |
| Boot disk | Ubuntu 20.04 LTS |
| Size boot disk | 20 GB |
| Firewall | Allow HTTP traffic & Allow HTTPS traffic 
| Network-tag | allow-ports-jupyter-8888


## set up on vm
    sudo apt-get update
### install pip ( package manager python )
    sudo apt install python3-pip
