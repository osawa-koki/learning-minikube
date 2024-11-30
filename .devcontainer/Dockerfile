FROM ubuntu:24.04

# Create the user
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Update and install required packages first
RUN apt-get update \
    && apt-get install -y sudo \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Create the user with a different UID and GID if 1000 is taken
RUN if id -u 1000 >/dev/null 2>&1 || getent group 1000 >/dev/null 2>&1; then \
        USER_UID=2000; \
        USER_GID=2000; \
    fi \
    && groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Switch to the user
USER $USERNAME
