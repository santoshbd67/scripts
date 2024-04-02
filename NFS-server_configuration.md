# ON SERVER SIDE
sudo apt update
sudo apt install nfs-kernel-server
sudo mkdir /srv/nfs_share
sudo nano /etc/exports
/srv/nfs_share  <client_ip>(rw,sync,no_subtree_check)
Replace <client_ip> with the IP address of the NFS client. You can use * to allow any client to access the shared directory.
sudo exportfs -a
sudo systemctl restart nfs-kernel-server
note * give all permission to directory

# On Client Side

sudo apt update
sudo apt install nfs-common
sudo mkdir /mnt/nfs_share
sudo mount -t nfs <server_ip>:/srv/nfs_share /mnt/nfs_share

