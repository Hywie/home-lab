# Setup

## File System
data
├── downloads
└── media
     ├── movies
     └── tv

## Steps to perform on the host machine
1. Create the data directory.
`sudo mkdir data`
2. Optional: Mount to NFS drive
`sudo mount -t nfs <NAS IP>:/media-data /data`

3. Give data permissions
```bash
sudo chown -R $USER:$USER /data
sudo chmod -R a=,a+rX,u+w,g+w /data
```
