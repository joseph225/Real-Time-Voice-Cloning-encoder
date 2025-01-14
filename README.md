# Real-Time Voice Cloning


SV2TTS is a deep learning framework in three stages. In the first stage, one creates a digital representation of a voice from a few seconds of audio. In the second and third stages, this representation is used as reference to generate speech given arbitrary text.

Google Colab implementation can be found [here](https://colab.research.google.com/drive/1Bm3Sx6aIhPWgLGIJwxjN1o_h-79_6G8L#scrollTo=2z6kilrQW6Em)

## Setup

### 1. Install Requirements
1. Both Windows and Linux are supported. A GPU is recommended for training and for inference speed, but is not mandatory.
2. Python 3.7 is recommended. Python 3.5 or greater should work, but you'll probably have to tweak the dependencies' versions. I recommend setting up a virtual environment using `venv`, but this is optional.

   #### To install Python3.7 -
   1. $ sudo apt update
   2. $ sudo apt install software-properties-common
   3. $ sudo add-apt-repository ppa:deadsnakes/ppa
   4. $ sudo apt install python3.7
    
   #### To setup virtual environment -
   1. $ sudo apt install python3.7-venv
   2. $ python3.7 -m venv env37
   3. $ source env37/bin/activate
   4. $ deactivate (when done using the environment)

3. Install [ffmpeg](https://ffmpeg.org/download.html#get-packages). This is necessary for reading audio files.
4. Install [PyTorch](https://pytorch.org/get-started/locally/). Pick the latest stable version, your operating system, your package manager (pip by default) and finally pick any of the proposed CUDA versions if you have a GPU, otherwise pick CPU. Run the given command.
5. Install the remaining requirements with `pip install -r requirements.txt`

### 2. (Optional) Download Pretrained Models
Pretrained models are now downloaded automatically. If this doesn't work for you, you can manually download them [here](https://github.com/CorentinJ/Real-Time-Voice-Cloning/wiki/Pretrained-models).

### 3. (Optional) Test Configuration
Before you download any dataset, you can begin by testing your configuration with:

`python demo_cli.py`

If all tests pass, you're good to go.

### 4. (Optional) Download Datasets
For playing with the toolbox alone, I only recommend downloading [`LibriSpeech/train-clean-100`](https://www.openslr.org/resources/12/train-clean-100.tar.gz). Extract the contents as `<datasets_root>/LibriSpeech/train-clean-100` where `<datasets_root>` is a directory of your choosing. Other datasets are supported in the toolbox, see [here](https://github.com/CorentinJ/Real-Time-Voice-Cloning/wiki/Training#datasets). You're free not to download any dataset, but then you will need your own data as audio files or you will have to record it with the toolbox.

### 5. Launch the Toolbox
You can then try the toolbox:

`python demo_toolbox.py -d <datasets_root>`  
or  
`python demo_toolbox.py`  

depending on whether you downloaded any datasets. If you are running an X-server or if you have the error `Aborted (core dumped)`, see [this issue](https://github.com/CorentinJ/Real-Time-Voice-Cloning/issues/11#issuecomment-504733590).

## Known Issues

1. Delete empty directories(not containing .npy files) from <dataset_root>/SV2TTS/encoder/ after the encoder pre-processed the dataset before starting the encoder training. (you may use : $ find <dataset_root>/SV2TTS/encoder/* -empty to find empty folders)

## Additional help 

1. Starting visdom server
   python3 -m visdom.server
   
   Then, in your browser, you can go to:

   http://localhost:8097
   
   More on Visdom setup and details can be found [here](https://github.com/fossasia/visdom/blob/master/README.md).
   
2. To train from scratch, follow this link [here](https://github.com/CorentinJ/Real-Time-Voice-Cloning/wiki/Training).
