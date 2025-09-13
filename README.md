# VoiceAI
An AI-powered Call Quality Analyzer built in Google Colab. It transcribes call recordings, identifies speakers, and extracts key metrics like talk-time ratio, sentiment, and actionable insights

# Brief Explanation
Our approach utilizes a multi-stage, API-first pipeline to analyze call recordings efficiently within the Google Colab environment. The process begins by extracting the raw audio from the source YouTube link using the pytubefix library and converting it to a standardized WAV format with ffmpeg for optimal processing.

For the core tasks of transcription and speaker identification (diarization), we leverage the AssemblyAI Speech-to-Text API. This choice was made to ensure high accuracy with poor audio quality and to meet the sub-30-second processing requirement. The API is configured to return a structured transcript that includes speaker labels, timestamps, sentiment analysis, and a generated summary.

The resulting structured data is then parsed using Python. We calculate the talk-time ratio and longest monologue from the speaker-specific utterance timestamps. A simple heuristic scoring system—based on talk duration, question count, and speaking order—is used to accurately identify the roles of "Sales Rep" and "Customer". The final report aggregates these metrics into a clear, concise summary of the call's quality and dynamics.

# Key Libraries and APIs
AssemblyAI API: This is the central engine of the project. It's a cloud-based Speech-to-Text API used for several critical tasks simultaneously:

Automatic Speech Recognition (ASR): Converting the call's audio into a written transcript.

Speaker Diarization: Identifying "who spoke when" by segmenting the audio and assigning speaker labels (e.g., Speaker A, Speaker B).

Sentiment Analysis: Analyzing the transcribed text to determine the emotional tone (Positive, Negative, Neutral) of each sentence.

Abstractive Summarization: Generating a concise summary of the call to serve as an "actionable insight."

pytubefix: A community-maintained fork of the pytube library, used to reliably download audio streams from YouTube links.

ffmpeg-python: A Python wrapper for the powerful FFmpeg tool. It was used to convert the downloaded audio from its original format into a standardized, single-channel (mono) WAV file, which is the optimal format for most speech recognition systems.
