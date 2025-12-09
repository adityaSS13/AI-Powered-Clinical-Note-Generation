# AI-Powered-Clinical-Note-Generation
This project focuses on processing a transcript of a patient-doctor interaction (or a long, transcribed diagnostic report) and transforming it into a standardized clinical note format, following the SOAP structure.  
For converting audio to text (transcribing audio), OpenAI's open source Speech Recognition model 'Whisper' (whisper-medium.en) has been used (along with Huggingface pipelines API). Also, the use of closed source 'gpt-4o-mini-transcribe' model has been shown (OpenAI API key needs to be purchased and included in the .env file, or added to Google Colab's 'secrets' field).  

Steps:  
- Download any sample mp3 file of a conversation between between a doctor and a patient (Kaggle or any other source)
- Create a Huggingface token and add it to .env file/Google colab secrets (key-value pair). The key name should be 'HF_TOKEN'
- For using the Llama 3.1 model, navigate to this webpage and agree with all the necessary terms and conditions: https://www.google.com/url?q=https%3A%2F%2Fhuggingface.co%2Fmeta-llama%2FMeta-Llama-3.1-8B

Key features:
1. Audio Transcription: Supports transcription via the Hugging Face Pipeline (using the openai/whisper-medium.en model) and the OpenAI API (gpt-4o-mini-transcribe).
2. Large Language Model (LLM): Employs the Meta-Llama/Llama-3.1-8B-Instruct model for generating minutes from the transcript.
3. Efficient Deployment: The LLM is loaded with 4-bit quantization using BitsAndBytesConfig and optimized for a T4 GPU runtime.
4. Structured Output: The model is prompted to generate a note following a common structure like SOAP (Subjective, Objective, Assessment, Plan):
   - (S)ubjective: The patient's chief complaint
   - (O)bjective: Vital signs, key physical exam findings, and critical lab/imaging results mentioned.
   - (A)ssessment: The final diagnosis or differential diagnoses discussed.
   - (P)lan: Medication changes, follow-up appointments, or lifestyle advice given.
