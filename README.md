<img src='imgs/teaser.gif' align="right" width=360>

<br><br><br><br>

# IR 2 RGB video translation

From vid2vid (https://github.com/NVIDIA/vid2vid)

## Prerequisites
- Linux or macOS
- Python 3
- NVIDIA GPU + CUDA cuDNN
- PyTorch 0.4+


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
- Must be in the following format: 

	```
	- dataset 
		|
		+- train_A # input training IR images
		+- train_B # output training RGB images
		+- test_A # input test IR images
		+- test_B # output test RGB images
	```

