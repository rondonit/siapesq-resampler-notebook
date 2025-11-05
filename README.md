# SIAPESQ Resampler Notebook

A Jupyter notebook implementation for NetCDF file resampling and regridding.

## Features

- Interactive Jupyter environment for data processing
- Support for NetCDF (.nc) file resampling
- Spatial regridding capabilities using ESMF/ESMPy
- Built on robust scientific Python stack

## Requirements

All dependencies are managed through conda/micromamba. The main requirements include:

- Python 3.11
- xarray >= 2024.6
- esmf >= 8.5
- xesmf >= 0.8
- Other scientific packages (numpy, pandas, etc.)

## Installation

### Using Binder

Click the Binder badge below to launch the notebook in your browser:

[Add Binder badge here]

### Local Installation with Docker

1. Clone this repository:
```bash
git clone [repository-url]
cd siapesq-resampler-notebook
```

2. Build and run the Docker container:
```bash
docker build -f docker/Dockerfile -t siapesq-resampler .
docker run -p 8888:8888 siapesq-resampler
```

3. Open `http://localhost:8888` in your browser to access JupyterLab

### Manual Installation

1. Create a conda environment using the provided environment.yml:
```bash
conda env create -f binder/environment.yml
```

2. Activate the environment:
```bash
conda activate resampler-env
```

3. Launch JupyterLab:
```bash
jupyter lab
```

## Environment Variables

The following environment variables are automatically configured to optimize ESMF performance:

- `OMP_NUM_THREADS=1`
- `OPENBLAS_NUM_THREADS=1`
- `MKL_NUM_THREADS=1`
- `NUMEXPR_NUM_THREADS=1`
- `ESMF_LOGFILE=ESMF_LOG`

## License

[Add license information here]

## Contributing

[Add contribution guidelines here]