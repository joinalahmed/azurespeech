# Azure Speech Diarization

A Python script that performs real-time speaker diarization using Azure Cognitive Services Speech SDK. The application transcribes conversations and identifies different speakers in an audio file.

## Features

- Real-time speech-to-text transcription
- Speaker diarization (identification of different speakers)
- Support for intermediate diarization results
- Event-based architecture for handling transcription events
- Support for multiple audio languages

## Prerequisites

- Python 3.7 or later
- Azure subscription
- Azure Speech resource (key and region)
- Microsoft Visual C++ Redistributable for Visual Studio 2015, 2017, 2019, and 2022
- For Linux: x64 target architecture support

## Installation

1. Install the Azure Speech SDK:
```bash
pip install azure-cognitiveservices-speech
```

2. Set up environment variables:
```bash
# Windows
set SPEECH_KEY=your-key
set SPEECH_REGION=your-region

# Linux/MacOS
export SPEECH_KEY=your-key
export SPEECH_REGION=your-region
```

## Usage

1. Place your audio file in the project directory (default filename: "katiesteve.wav")

2. Run the application:
```bash
python conversation_transcription.py
```

The application will output:
- Intermediate transcription results with speaker IDs
- Final transcribed text with speaker identification
- Session events (start, stop, cancellation)

## Configuration Options

### Language Settings
Change the speech recognition language by modifying:
```python
speech_config.speech_recognition_language="en-US"
```
Supported languages include:
- en-US (English, United States)
- es-ES (Spanish, Spain)
- And many more...

### Audio Input
Modify the audio input file:
```python
audio_config = speechsdk.audio.AudioConfig(filename="your-audio-file.wav")
```

## Output Format

The application provides two types of output:

1. Intermediate Results (TRANSCRIBING):
```
TRANSCRIBING:
        Text={transcribed_text}
        Speaker ID={speaker_id}
```

2. Final Results (TRANSCRIBED):
```
TRANSCRIBED:
        Text={transcribed_text}
        Speaker ID={speaker_id}
```

Speaker IDs are assigned as "Guest-1", "Guest-2", etc., for different speakers in the conversation.

## Error Handling

The application includes error handling for:
- Session cancellation
- Recognition failures
- Configuration errors
- File access issues
