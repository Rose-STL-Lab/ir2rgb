
# IR 2 RGB video translation

From vid2vid (https://github.com/NVIDIA/vid2vid)

## Prerequisites
- Linux or macOS
- Python 3
- GCC version <= 6
- NVIDIA GPU + CUDA cuDNN
- PyTorch 0.4+

## Additional downloads 
- The file `FlowNet2_checkpoint.pth.tar` is too large to upload to github and needs to be downloaded seperately. It contains the FlowNet2 model and is used to construct the flow model for vid2vid
- To download the model run `python scripts/download_models_flownet2`. Now try training the ir2rgb network.
- If you have any additional errors and need to compile a snapshot of the FlowNet2:
	- First try with the scripts I made for this repo. Go to the location `ir2rgb/models/flownet2_pytorch/` and run the command line: `bash install.sh` (or run each command inside `install.sh` in the command line individually).
		- If your gpu's are not accounted for in this compilation, you might have to add their arch codes: Add the line '-gencode', 'arch=compute_XX,code=sm_XX', (where XX is GPU specific) in all 3 setup.py scripts in `channelnorm_package`, `correlation_package`, and `resample2d_package`. Then install flownet.
	- If even this doesn't work, you might have install it from scratch: first go to: https://docs.google.com/uc?export=download&id=1gKwE1Ad41TwtAzwDcN3dYa_S6DcVyiSl and download `flownet2_pytorch_041.zip`. To compile:
		- Unzip and copy the entire content of the extracted `flownet2_pytorch_041.zip` file to the location `ir2rgb/models/` (and replace any existing files with the same names)
		- Then go to the location `ir2rgb/models/flownet2_pytorch/` and run the command line: `bash install.sh` (or run each command in `install.sh` in the command line individually)
	- For more information please see: https://github.com/NVIDIA/vid2vid/issues/86 and https://github.com/NVIDIA/vid2vid/issues/82 

### Training 

- To train the model, from the command line run
    ```
    python train.py --name Name_of_training_session --dataroot sample_dataset --input_nc 3 --output_nc 3 --tf_log
    ```
  - Or, simply bash the script (which contains the command line)
    ```
    bash run_to_train.sh
    ```  
### Testing

- To test the model, from the command line run
    ```
    python test.py --name name_of_test_session --dataroot sample_dataset --input_nc 3 --output_nc 3 --use_real_img
    ```
  - Or, simply bash the script (which contains the command line)
    ```
    bash run_to_test.sh
    ```  
- For a detailed list of options, please see the options folder

### Dataset
- Dataset folder must be in the following format: 

	```
	.
	├── dataset_folder    
		│
		├── train_A    # input training IR images
		├── train_B    # output training RGB images
		├── test_A     # input test IR images
		└── test_B     # output test RGB images
	```

