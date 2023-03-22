# node-typescript-samba

this is a modified VSCode Dev Container definition. The base is derived from Microsoft's node-typescript reference example :
https://github.com/devcontainers/images/tree/main/src/typescript-node

It has been modified to serve the /workspaces and /home/node directories via SMB on localhost so that non-VSCode tooling can also be used. the SBM share
allows guest read / write access so no user or password is needed. 

This container is not intended to be used as a deployment container due to the SMB share. 

After the container is spun up it will assign the SMB port 445 to a random port on localhost. the VSCode ports view will show you which port to use to connect
to the SMB share. this port will change each time you spin up the container. 
