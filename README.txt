Project Description

This project is an initial step towards creating an AI which can generate musical notes based on an input musical segment.

In its current structure, the first step is to use Spleeter by Deezer, which a Python library using Tenserflow with pretrained models for source separation.

Next step involved is to generate audio with GANSynth with generative adversarial networks. Details are in the original ICLR 2019 Paper in this link https://openreview.net/forum?id=H1xQVn09FX

Notebooks:

1- spleeter.ipynb

spleeter.ipynb is a Google Colab notebook which uses Audio from IPython.display module that created an audio object in order to display Audio controls in the frontend.

Next, to separate the audio file into various stems, the code uses Spleeter library to create trained state of the art models for performing various versions of separation.

2- vg_ganSynth.ipynb

A Google LLC notebook of a demo GANSynth to generate audio with Generative Adversarial Networks. Individual instrument notes are produced by GANSynth.
Various instrument tempers are represented by usage of latent space of the learned generator, having the pitch as the conditional attribute.
Audio examples: http://goo.gl/magenta/gansynth-examples



The code first setup the environment in section 1 by installing magneta, downloading the model, and defining helper functions.

Libraries used: 
	- os
	- google.colab
	- librosa
	- load_audio
	- flags
	- generate_util
	- model
	- util
	- matplotlib
	- note-seq
	- numpy
	- tenserflow
Functions:
	- upload():
		takes .wav file path as input
		returns a list (file_list) 
	- load_midi():
		a helper function that loads midi as a notesequence 
		returns ns and notes 
	- get_evelope()
		helper function
		Create an attack sustain release amplitude envelope.
	- combine_notes():
		helper function
		Combine audio from multiple notes into a single audio clip.

  		Args:
    			audio_notes: Array of audio [n_notes, audio_samples].
    			start_times: Array of note starts in seconds [n_notes].
    			end_times: Array of note ends in seconds [n_notes].
    			sr: Integer, sample rate.

  		Returns:
    			audio_clip: Array of combined audio clip [audio_samples]
	- specplot():
		plotting tool

Section 2(a): Random Interpolation

Next cell of code in the notebook results instrumental sounds the morph sin smoother and slower morph between one another.
Prior to the resulted sounds, interpolation between random equally spaced in time latent vectors of a full song's MIDI. 
The cell provides an option to upload/choose your own midi file. Afterwards, the synthesized audio's Constant-Q spectrogram is displayed and played.

section 2(b) of the notebook provides the ability to interpolate between two latent vectors over a MIDI clip, specify number of random instruments from 4 to 16, and finally generate custom interpolation.

References: 

1- “Magenta/Magenta.” GitHub, 21 Oct. 2021, github.com/magenta/magenta/blob/main/magenta/models/gansynth/README.md. Accessed 21 Oct. 2021.

2- “GANSynth: Making Music with GANs.” Magenta, magenta.tensorflow.org/gansynth.

3- “Spleeter.” Research.deezer.com, research.deezer.com/projects/spleeter.html. Accessed 21 Oct. 2021.
		
