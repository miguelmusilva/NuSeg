Nuclei Segmentation on Fixed Data
==========

Overview 
--------

Installation
--------
Use the "stardist_sdeblank_conda_env.yml" file to set up the environment
```ruby
conda env create -f stardist_sdeblank_conda_env.yml
```

For general functions and module for handling files, clone or download ZIP "Rios" GitHub from SdeBlank. Once you activate "StarDist" environment, use next command in this folder to install all modules. 
```ruby
pip install -e .
```

The nuclei segmentation will be done by StarDist Deep Learning. Clone or download ZIP "deep_learning" repository from SdeBlank's GitHub. Once you activate "StarDist" environment, use next command to install all modules.
```ruby
pip install -e .
```

Usage
--------
The main script to run is stardist_model.py ("../deep_learning-main/deep_learning/stardist/stardist_model.py")

Provide:

- -p | --predict : provide with the image path that needs to be segmented. If the image is .h5 file, provide the substructure itself (e.g. "name.h5/image"). The DAPI channel must be normalized. 
- -m | --model : provide with the path to the stardist checkpoint trained. Inside of the StarDistModel folder, two files are left because of their size (weights_best.h5 and weights_last.h5). Both files are saved on the computer.
- -o | -- output : output folder where to store segmented file (name is based on the input file)
- --tiled : OPTIONAL. For large files, perform prediction in tiles

```ruby
python scripts/stardist_model.py \
       --predict .../name.h5/image \
       --model 93_StarDistModel_HyperparameterTuning \
       --output ../.. \
       --tiled --tile_size_xy 640  
```

Output file:

- A ".h5" segmented fixed image (e.g. "name.h5/segments")
