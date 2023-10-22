# Emergent Language in Multi-Step Bidirectional Reference Game

## Description

## Requirements
[optional] = "You can skip this step!"

1. Setting up the environment. 
    * Recreate the environment: `conda env create --name myenv --file environment.yml`
    * Activate conda env: `conda activate --name`
    * [optional] Update `environment.yml`:
        - `echo "  - new-package1=1.2.3" >> environment.yml`
        - `conda env update --name myenv --file environment.yml`

2. [optional] The project contains large files. Before running the `main.py`, get acquatend with Git LFS.
    * Install Git LFS: `git lfs install`
    * Track large files: `git lfs track "folder/*"` and `git add .gitattributes` if file doesn't exist, then `git commit -m "Track file with Git LFS"`
    * Commit large files: `git add "folder/*"`
    * Push changes

    Useful once you push extracted image features or training results to a remote repository. 

3. Reposetory strucure.
| configs
| data
    | processed_data
| models
| training
| utils
    data_loader.py ---> loads COCO captions dataset, extracts features with ResNet50, 
                        and saves `train`, `test` and `val` datasets as `{ds}.tfrecord` files.

4. How to start the project.
    * [optional] Run `python3 utils/data_loader.py` to load the COCO caption dataset (requires at least 60 GB of free disk space). You may skip this step – extracted features are already saved under `data/processed_data` and will be further used in this project.

    * Run `python3 main.py` to execute the whole project:
        - `data_preprocessor.py` creates `R1` and `R2` image feature subsets along with one-hot encoded target vectors `t1` and `t2` that the model will be trained on;
        - `agent.py` runs the agent models;
        - `communication.py` is responsible for agent communication;
        - `training.py` is for training as well as evaluaton the test and validation datasets. It will also produce visualizations.
        - `args.py` sets the hyperparameters as lerning rate, number of epochs and batch sizes;
        - `settings.py` you can manually adjust other model parameters, such as embedding_size, scaling_factor, etc.


5. python main.py --learning-rates 0.001 0.0001 --batch-sizes 32 64 --epochs 50 100
