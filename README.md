# Key-Frame-Proposal-Network-for-Efficient-Pose-Estimation-in-Videos

Paper: https://arxiv.org/abs/2007.15217

This is the official implementation for ECCV20 paper: Key Frame Proposal Network for Efficient Pose Estimation in Videos
All implementations are based on Pytorch and up to date

# ----Prerequires----

python > 3.5

pytorch > 0.4.0

cuda > cuda 9.0

# ----Usage-----
1. Downloading data: 1) Penn Action: http://dreamdragon.github.io/PennAction/
                      2) JHMDB:  http://jhmdb.is.tue.mpg.de/dataset 
                                 please refer https://github.com/lawy623/LSTM_Pose_Machines/blob/master/dataset/JHMDB/utils/getBox.m to generate bbox for later use

2. Downloading pre-train models: 1) We provided our best model for Penn Action, sub-JHMDB, and online updating experiments
                                 2) Please download models:  https://drive.google.com/drive/folders/13q-UGXGLCwMXzCRX6CeOyQ12dJziGyxT?usp=sharing [GoogleDrive]
                                                                                            
                                                                                            or                            
                                                              https://1drv.ms/u/s!AgyTrG_BdJ9GbTjqlTuFDSERUfo?e=EnPzkG  [OneDrive]
                                                             
                                 3) Please place models under folder 'models'
                                 
# NOTE: 
      1. Our demo code is implemented with our best model on validation set for each dataset 
      2. Our implementations are able to integrate other Resnet backbones 
      3. We updated our Human Pose Interpolation Module, instead of using Least-Square solution in paper, we implemented with FISTA that is able to integrate into deep network for later use. Results were improved with comparable running time.  
      Details of FISTA can be found: https://people.rennes.inria.fr/Cedric.Herzet/Cedric.Herzet/Sparse_Seminar/Entrees/2012/11/12_A_Fast_Iterative_Shrinkage-Thresholding_Algorithmfor_Linear_Inverse_Problems_(A._Beck,_M._Teboulle)_files/Breck_2009.pdf
      
      4. For more details of our dynamic-based dictionary, please refer : https://openaccess.thecvf.com/content_ECCV_2018/papers/Wenqian_Liu_DYAN_A_Dynamical_ECCV_2018_paper.pdf

# -----Details------

1. Training: 1) We provded training files for each of experiments
             2) For training Penn Action and Sub-JHMDB: please not, parameter 'alpha' that we disscussed in our paper is linearly increasing with the training epoch, you may need to tune by yourself while training. 
             3) For online updating experiment on sub-JHMDB: we used our best model as the backbone
             
2. Testing: 1)We provded testing files for each of experiments, all results reported in Table 3,4,5 were based on the baseline, we directly applied their model on both Penn Action and sub-JHMDB dataset, no fine-tuning involved
            2) Please refer https://github.com/microsoft/human-pose-estimation.pytorch, we used architecture of '384x384_pose_resnet_101_d256d256d256' which trained on MPII     
             3) You can find 'sampling comparison' experiment in 'test_penn.py', and 'robustness comparison' experiment in 'test_jhmdb.py'
             4) Note: set 'if_occ' is 'True' for doing 'robustness comparison' experiment, and you can change occlusion ratio by setting 'occRatio'
              
 
 



