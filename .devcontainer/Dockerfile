FROM jupyter/base-notebook:lab-3.6.2

# Ensure that all users have read-write access to all files created in the subsequent commands.
ARG DOCKERFILE_UMASK=0000

# Install the Conda packages.
COPY --chown=$MAMBA_USER:$MAMBA_USER environment.yml /tmp/environment.yml
RUN : \
    # Configure Conda to use the conda-forge channel
    && mamba config append channels conda-forge \
    # Install and clean up
    && mamba install --yes --name base --file /tmp/environment.yml \
    && mamba clean --all --yes;

# Activate the conda environment for the Dockerfile.
# <https://github.com/mamba-org/micromamba-docker#running-commands-in-dockerfile-within-the-conda-environment>
ARG MAMBA_DOCKERFILE_ACTIVATE=1

