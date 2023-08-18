FROM jupyter/base-notebook:lab-3.6.2

# name your environment and choose the python version
ARG env_name=musa-550-fall-2023
ARG py_ver=3.10.12


# alternatively, you can comment out the lines above and uncomment those below
# if you'd prefer to use a YAML file present in the docker build context

COPY --chown=${NB_UID}:${NB_GID} environment.yml /tmp/
RUN mamba env create -p "${CONDA_DIR}/envs/${env_name}" -f /tmp/environment.yml && \
    mamba clean --all -f -y

# create Python kernel and link it to jupyter
RUN "${CONDA_DIR}/envs/${env_name}/bin/python" -m ipykernel install --user && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"


# if you do not want this environment to be the default one, comment this line
# hadolint ignore=DL3059
RUN echo "conda activate ${env_name}" >> "${HOME}/.bashrc"