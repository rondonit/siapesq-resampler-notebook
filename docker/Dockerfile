FROM mambaorg/micromamba:2.3.3

# Using the same environment.yml from Binder to build the Docker image for local testing
COPY binder/environment.yml /tmp/environment.yml
RUN micromamba create -n resampler-env -f /tmp/environment.yml && \
    micromamba clean -a -y

# ESMF configuration to avoid some common issues
ENV OMP_NUM_THREADS=1 \
    OPENBLAS_NUM_THREADS=1 \
    MKL_NUM_THREADS=1 \
    NUMEXPR_NUM_THREADS=1 \
    ESMF_LOGFILE=ESMF_LOG

# Uses bash as default shell
SHELL ["/bin/bash", "-lc"]
# Activate the environment by default
RUN echo "micromamba activate resampler-env" >> ~/.bashrc

# Ensure micromamba cache dir exists and is writable by any UID (helps when running with -u)
RUN mkdir -p /home/mambauser/.cache/mamba/proc && \
    chmod -R a+rwX /home/mambauser/.cache
ENV XDG_CACHE_HOME=/home/mambauser/.cache

# Set working directory and copy notebook files
WORKDIR /workspace
RUN chown -R mambauser:mambauser /workspace
COPY . .

# Expose Jupyter Notebook port
EXPOSE 8888

# Start Jupyter Notebook server
CMD micromamba run -n resampler-env jupyter lab --ip=0.0.0.0 --no-browser --NotebookApp.token=''

