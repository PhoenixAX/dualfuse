# dualfuse
## Installation
### Requirements
- pytorch >= 1.8 
- yaml
- easydict
- pyquaternion
- [lightning](https://github.com/Lightning-AI/lightning) (tested with pytorch_lightning==1.3.8 and torchmetrics==0.5)
- [torch-scatter](https://github.com/rusty1s/pytorch_scatter) (pip install torch-scatter -f https://data.pyg.org/whl/torch-1.9.0+${CUDA}.html)
- [nuScenes-devkit](https://github.com/nutonomy/nuscenes-devkit) (optional for nuScenes)
- [spconv](https://github.com/traveller59/spconv) (tested with spconv==2.1.16 and cuda==11.1, pip install spconv-cu111==2.1.16)
- [torchsparse](https://github.com/mit-han-lab/torchsparse) (optional for MinkowskiNet and SPVCNN. sudo apt-get install libsparsehash-dev, pip install --upgrade git+https://github.com/mit-han-lab/torchsparse.git@v1.4.0)
- torch_geometric==1.7.2
- tensorboard
- timm
- termcolor
- tensorboardX

### The Thirdparty File Data
- You can download the essential file from[here](https://github.com/dvlab-research/SphereFormer/tree/master/third_party/SparseTransformer).
- Than follow the SpTr: PyTorch Spatially Sparse Transformer Library's README.md to set up the envionment.

## Data Preparation

### SemanticKITTI Dataset
Please download the files from the [SemanticKITTI website](http://semantic-kitti.org/dataset.html) and additionally the [color data](http://www.cvlibs.net/download.php?file=data_odometry_color.zip) from the [Kitti Odometry website](http://www.cvlibs.net/datasets/kitti/eval_odometry.php). Extract everything into the same folder.
```
./dataset/
├── 
├── ...
└── SemanticKitti/
    ├──sequences
        ├── 00/           
        │   ├── velodyne/	
        |   |	├── 000000.bin
        |   |	├── 000001.bin
        |   |	└── ...
        │   └── labels/ 
        |   |   ├── 000000.label
        |   |   ├── 000001.label
        |   |   └── ...
        |   └── image_2/ 
        |   |   ├── 000000.png
        |   |   ├── 000001.png
        |   |   └── ...
        |   calib.txt
        ├── 08/ # for validation
        ├── 11/ # 11-21 for testing
        └── 21/
	    └── ...
```
### Data preprocessing


## Training
You can run the training with
```shell script
cd <dir path>
python main.py --log_dir 2DPASS_semkitti --config config/2DPASS-semantickitti.yaml --gpu 0
```
The output will be written to `logs/SemanticKITTI/2DPASS_semkitti` by default. 

## Testing
You can run the testing with
```shell script
cd <dir path>
python main.py --config config/2DPASS-semantickitti.yaml --gpu 0 --test --num_vote 12 --checkpoint <dir for the pytorch checkpoint>
```
The checkpoint path will be `logs/SemanticKITTI/2DPASS_semkitti` by default. 
