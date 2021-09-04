# Start from the code-server Debian base image
FROM linuxserver/code-server:latest

LABEL maintainer="Mohamed Elashri <muhammadelashri@gmail.com>"

USER root

# Use bash shell
ENV SHELL=/bin/bash

# Install apt packages
RUN apt-get update
RUN apt-get install -y cmake  vim emacs nano locales
RUN apt-get install -y python3 curl sudo net-tools git aria2


# Install unzip + rclone (For remote filesystem support )
RUN sudo apt-get update \
 && sudo apt-get install unzip -y
RUN curl https://rclone.org/install.sh | sudo bash

ENV LANG=en_US.utf8 \
    LANGUAGE=en_US.UTF-8 \
    LC_ALL=en_US.UTF-8

# Install a VS Code extension:
RUN code-server --install-extension eamodio.gitlens \
 && code-server --install-extension esbenp.prettier-vscode \
 && code-server --install-extension ms-python.python \
 && code-server --install-extension vscode-icons-team.vscode-icons \
 && code-server --install-extension GitHub.github-vscode-theme \
 && code-server --install-extension TabNine.tabnine-vscode \
 && code-server --install-extension kiteco.kite \
 && code-server --install-extension christian-kohler.path-intellisense \
 && code-server --install-extension HookyQR.beautify \
 && code-server --install-extension James-Yu.latex-workshop \
 && code-server --install-extension danielpinto8zz6.c-cpp-compile-run \
 && code-server --install-extension codezombiech.gitignore \
 && code-server --install-extension muhammadelashri.FHiCL \
 && code-server --install-extension sourcery.sourcery \
 && code-server --install-extension julialang.language-julia \
 && code-server --install-extension albertopdrf.root-file-viewer \
 && code-server --install-extension ms-azuretools.vscode-docker \

# Port
ENV PORT=8443

# Use our custom entrypoint script first
COPY entrypoint.sh /usr/bin/deploy-container-entrypoint.sh
ENTRYPOINT ["/usr/bin/deploy-container-entrypoint.sh"]
