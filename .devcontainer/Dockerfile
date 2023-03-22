# [Choice] Node.js version (use -bullseye variants on local arm64/Apple Silicon): 18, 16, 14, 18-bullseye, 16-bullseye, 14-bullseye, 18-buster, 16-buster, 14-buster
ARG VARIANT=16-bullseye
FROM mcr.microsoft.com/devcontainers/javascript-node:0-${VARIANT}

# Install tslint, typescript. eslint is installed by javascript image
ARG NODE_MODULES="tslint-to-eslint-config typescript ts-node"
RUN su node -c "umask 0002 && npm install -g ${NODE_MODULES}" \
    && npm cache clean --force > /dev/null 2>&1



# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment if you want to install an additional version of node using nvm
# ARG EXTRA_NODE_VERSION=10
# RUN su node -c "source /usr/local/share/nvm/nvm.sh && nvm install ${EXTRA_NODE_VERSION}"

# [Optional] Uncomment if you want to install more global node packages
 RUN su node -c "npm install -g firebase-tools"

# Install Samba and FTP server (vsftpd)
#RUN apt-get update && apt-get install -y samba vsftpd git
RUN apt-get update && apt-get install -y samba  git

# Copy Samba and FTP configuration files to the container
COPY smb.conf /etc/samba/smb.conf
#COPY vsftpd.conf /etc/vsftpd.conf

# Expose the ports for Samba and FTP
EXPOSE 137/udp 138/udp 139 445
#EXPOSE 20 21

# Start Samba and FTP services
#CMD service smbd start && service nmbd start && service vsftpd start && /bin/bash