# VoiceAI
An AI-powered Call Quality Analyzer built in Google Colab. It transcribes call recordings, identifies speakers, and extracts key metrics like talk-time ratio, sentiment, and actionable insights

# Brief Explanation
Our approach utilizes a multi-stage, API-first pipeline to analyze call recordings efficiently within the Google Colab environment. The process begins by extracting the raw audio from the source YouTube link using the pytubefix library and converting it to a standardized WAV format with ffmpeg for optimal processing.

For the core tasks of transcription and speaker identification (diarization), we leverage the AssemblyAI Speech-to-Text API. This choice was made to ensure high accuracy with poor audio quality and to meet the sub-30-second processing requirement. The API is configured to return a structured transcript that includes speaker labels, timestamps, sentiment analysis, and a generated summary.

The resulting structured data is then parsed using Python. We calculate the talk-time ratio and longest monologue from the speaker-specific utterance timestamps. A simple heuristic scoring system—based on talk duration, question count, and speaking order—is used to accurately identify the roles of "Sales Rep" and "Customer". The final report aggregates these metrics into a clear, concise summary of the call's quality and dynamics.

