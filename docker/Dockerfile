FROM continuumio/miniconda3:latest

# Faster, quieter conda and non-interactive installs
ENV DEBIAN_FRONTEND=noninteractive \
    CONDA_ALWAYS_YES=true \
    CONDA_CHANGEPS1=false \
    PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# WORKDIR /app

# Copy only the env spec first to leverage Docker layer caching
COPY environment.yml /tmp/environment.yml

# Create the environment (name is taken from environment.yml)
RUN conda env create -f /tmp/environment.yml \
    && conda clean -a -y

# Make the env the default for subsequent RUN/CMD (no need for `conda activate`)
# Replace `myenv` with the env name defined in environment.yml
SHELL ["conda", "run", "-n", "env_robot", "/bin/bash", "-c"]

# Copy your project code
# COPY . /app


