FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu

RUN mkdir -p /home/codespace/.kitclient
RUN git clone https://gitlab.com/hfossedu/kits/KitClient.git /home/codespace/.local/lib/kitclient
RUN chmod +x /home/codespace/.local/lib/kitclient/src/install-kit-features-into-client.sh
RUN sudo ln -s /home/codespace/.local/lib/kitclient/src/install-kit-features-into-client.sh /usr/share/git-core/templates/hooks/post-checkout
RUN cat /home/codespace/.local/lib/kitclient/src/bashrc.additions >> /home/codespace/.bashrc
RUN mkdir -p "$HOME/.kitclient"
RUN git config --global user.name > "$HOME/.kitclient/kituser.txt"
RUN git config --global --add safe.directory "${PROJ_ROOT}"
RUN git config --global pull.ff only
# RUN git config --global credential.helper store
RUN git config --global init.defaultBranch main
RUN git config --global merge.conflictstyle diff3
RUN git config --global merge.tool vscode
RUN git config --global mergetool.keepbackup false
RUN git config --global mergetool.vscode.cmd 'code --wait $MERGED'