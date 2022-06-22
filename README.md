# MTUCI_Praktika_2022
Keyword in audio recognition via Wav2KWS SOTA model


Preparaton:
1. Download main repo https://github.com/qute012/Wav2Keyword. Contrary to instructions there - you don't have to install fairseq locally
2. I used CUDA 10.2 for my project. Necessary PyTorch version is 1.7.0 Please install it via
pip3 install torch==1.7.0 torchvision==0.8.1 -f https://download.pytorch.org/whl/cu102/torch_stable.html

Other requirements are easy to install via pip. If you have problems with hydra: "pip install hydra-core" or download wheel manually; if you have problems with fairseq: "pip install fairseq==0.10"


Training:
1. Create a dataset directory with two folders: training and testing. In each of these folders add folders with class names and fill these class-named folders with .wav examples. Files in training will be used for training; files in testing will be used for validation. 

*Idk why - it just works that way*

par example:
```
-dataset_MTUCI
 --training
  ---privet
  ---kakdela
  ---horoso
  ---goodbuy
 --testing
  ---privet
  ---kakdela
  ---horoso
  ---goodbuy
```
 2. Open downstream_kws.py file and write your classes' names in array CLASSES at line 92 as they are written in directory. "unknown" and "silence" classes should be put in the beginning respectively.
 
 par example: CLASSES = 'unknown, silence, privet, kakdela, horosho, goodbuy'.split(', ')
 
 3. Run downstream_kws.py in cmd and write command in following terms:
 python downstream_kws.py [pretrained model path] [dataset directory path] [saving model weights path]
 
 par example:
 python downstream_kws.py wav2vec_small.pt dataset_MTUCI saved_model
 
 
 Inference:
 1. Open infer_real.py file and write your classes' names in array CLASSES at line 92.
 2. Locate .pth trained file at generated folder checkpoint/[saving model weights path]/weights_file.pth
 3. Run infer_real.py in cmd and write command in following terms:
 python infer_real.py [pretrained model path] [test_dataset directory path] [saved_model_weights_file_path]
 
 par example:
 python infer_real.py wav2vec_small.pt dataset_MTUCI_test checkpoint/[saving model weights path]/weights_file.pth
