# Speech-to-Speech Translation Pipeline Commands

## Step 1: Record Live Audio
```bash
termux-microphone-record -f ~/storage/shared/input5.wav -l 100
```
## Audio Preprocessing
```bash
ffmpeg -y -i ~/storage/shared/input5.wav -ar 16000 -ac 1 -c:a pcm_s16le ~/storage/shared/input5_fixed.wav
```
## Speech to Hindi Text
```bash
./build/bin/whisper-cli -m models/ggml-tiny.bin -f ~/storage/shared/input5_fixed.wav -l hi -nt -otxt -of hindi

cat hindi.txt
```
## Speech to English Translation
```bash
./build/bin/whisper-cli -m models/ggml-tiny.bin -f ~/storage/shared/input5_fixed.wav -tr -nt -otxt -of english

cat english.txt
```
## English Text to Speech
```bash
espeak -f english.txt -w ~/storage/shared/output_english.wav
```
## Play Output Audio
```bash
termux-media-player play ~/storage/shared/output_english.wav
```
