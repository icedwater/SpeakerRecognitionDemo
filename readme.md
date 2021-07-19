# Speaker Recognition Demo

This code is modified based on https://github.com/clovaai/voxceleb_trainer, and includes the pre-trained model.

## What it can do ?
This code can output the recognition score comparing a test utterance (with a speaker you wish to identify) with enrolled utterances (the utterances you have registered with known speakers) based on the person's unique voiceprint.

## How to use ?

### Clone the code:

    git clone https://github.com/icedwater/SpeakerRecognitionDemo

### Input: 
  
  Put the wav files you have registered in the `data/enrollment_audio` folder. Put the wav file you want to test in `data/test_audio` folder (You can put multiple test audio files, each test audio will generate one score list).

### Command:

    python demoSpeakerNet.py

### Output: 
  
  The speaker recognition score is a sort of difference score between the test utterance and all enrolled utterances. Utterances from the same speaker will tend to yield a higher score (the highest is 0.0).
  
  For instance: There are 7 audio files in `data/enrollment_audio` and 1 audio in `data/test_audio`. You can get the following output:


|    |     A1 |
| -- | ------ |
| A2 | -0.8122|
| D2 | -1.2551|
| D1 | -1.2641|
| B1 | -1.3041|
| C2 | -1.3062|
| B2 | -1.3246|
| C1 | -1.3756|

	
`A1` and `A2` come from the same speaker, so that pair will have the highest score.

## Other issue:

- Audio file format

	Current only wav, any sampling rate, single/dual channel is fine. 

- Requirements

	Pytorch (>=1.6.0), pandas, soundfile package
	
- GPU
	
	This is just the demo code, so the default setting is to use cpu only. It will not be very slow.

- Threshold setting

	It depends on the dataset. Just for suggestion: usually the score between 0 to -1.0 can be viewed as the same speaker, score below -1.0 can be viewed as different speaker.

- Reference

	Please check their paper for more details:

	```
	@inproceedings{chung2020in,
	  title={In defence of metric learning for speaker recognition},
	  author={Chung, Joon Son and Huh, Jaesung and Mun, Seongkyu and Lee, Minjae and Heo, Hee Soo and Choe, Soyeon and Ham, Chiheon and Jung, Sunghwan and Lee, Bong-Jin and Han, Icksang},
	  booktitle={Interspeech},
	  year={2020}
	}
	```
