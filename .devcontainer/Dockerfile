FROM mcr.microsoft.com/devcontainers/base:bullseye

ARG USERNAME=vscode

# Used to persist bash history as per https://code.visualstudio.com/remote/advancedcontainers/persist-bash-history
RUN SNIPPET="export PROMPT_COMMAND='history -a' && export HISTFILE=/commandhistory/.bash_history" \
    && mkdir /commandhistory \
    && touch /commandhistory/.bash_history \
    && chown -R $USERNAME /commandhistory \
    && echo "$SNIPPET" >> "/home/$USERNAME/.bashrc"

# install jless (because its not available at https://containers.dev/features at time of writing)
RUN NONINTERACTIVE=1 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" \
        && (echo; echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"') >> /home/vscode/.profile \
        && eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" \
        && brew install jless

