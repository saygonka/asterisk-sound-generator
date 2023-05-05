# Library for

## Create audio files

### Prerequisites

#### Using Coqui TTS

1. Install python.
2. Install Coqui TTS by running `pip install TTS`.

More details: [Coqui TTS Github Repo](https://github.com/coqui-ai/TTS)

#### Using Google Text to Speech

1. Create a service account for the Google Text to Speech API.
2. Create a key pair for the service account and download the JSON file.
3. Create a .env file in the root directory of this project.
4. Add `GOOGLE_APPLICATION_CREDENTIALS=/path/to/your/key.json` to the .env file.

More details: [Using the Text-to-Speech API with Node.js](https://codelabs.developers.google.com/codelabs/cloud-text-speech-node#0)

## Create transcriptions

1. Create a .env file in the root directory of this project.
2. Add `DEEPL_AUTH_KEY=<your deepl api key><` to the .env file.

## Convert audio files

Using the ffmpeg binary to convert the sound files to supported audio codecs for Asterisk. The default audio sampling rate of the created sound files by the Google TTS API is 16000 HZ.

### Convert WAV to G.722 and G.711 (alaw, ulaw)

- Convert WAV to G.711 alaw `ffmpeg -i path/to/name.wav -ar 8000 -codec:a pcm_alaw -f alaw path/to/name.alaw`
- Convert WAV to G.711 ulaw `ffmpeg -i path/to/name.wav -ar 8000 -codec:a pcm_mulaw -f mulaw path/to/name.ulaw`
- Convert MP3 to G.722 `ffmpeg -i path/to/name.wav -ar 16000 path/to/name.g722`

### Just for testing

Convert audio files back to mp3 `ffmpeg -f mulaw -ar 24000 -i path/to/name.g711 -f mulaw path/to/name.mp3`

More details:

- [Google Audio Codecs](https://cloud.google.com/speech-to-text/docs/encoding)
- [Supported codecs Asterisk](https://wiki.asterisk.org/wiki/display/AST/Codec+Modules)
- [Supported codecs FreePBX](https://wiki.freepbx.org/display/DIMG/Supported+Codecs)
