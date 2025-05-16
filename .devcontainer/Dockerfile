# Use official Python 3.12.8 image as base
FROM python:3.12.8-bullseye

# Install system dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       build-essential \
    && rm -rf /var/lib/apt/lists/*

# Install JupyterLab globally
RUN pip install --no-cache-dir jupyterlab

# Create a non-root 'vscode' user to match Codespaces defaults
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME

# Switch to that user
USER $USERNAME

# Default workspace folder
WORKDIR /workspace