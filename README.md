# MTUCI_Praktika_2022
Keyword in audio recognition via Wav2KWS SOTA model


Preparaton:
1. Download main repo https://github.com/qute012/Wav2Keyword. Contrary to instructions there - you don't have to install fairseq locally
2. I used CUDA 10.2 for my project. Necessary PyTorch version is 1.7.0 Please install it via
pip3 install torch==1.7.0 torchvision==0.8.1 -f https://download.pytorch.org/whl/cu102/torch_stable.html
Other requirements are easy to install via pip. If you have problems with hydra: "pip install hydra-core" or download wheel manually; if you have problems with fairseq: "pip install fairseq==0.10"


Training:
1. Create a dataset directory with two folders: training and testing. In each of these folders add folders with class names and fill these class-named folders with .wav examples
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
 2. Open downstream_kws file and write your classes' names in array CLASSES at line 92.
 3. Open downstream_kws in cmd and write command in following terms:
 python downstream_kws.py [pretrained model path] [dataset directory path] [saving model weights path]
 
 par example:
 python downstream_kws.py wav2vec_small.pt dataset_MTUCI saved_model
 
 
 Inference:
 
