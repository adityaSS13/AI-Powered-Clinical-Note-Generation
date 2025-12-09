# AI-Powered-Clinical-Note-Generation
This project implements a full-stack AI pipeline to automatically transform raw patient-physician interaction audio/transcripts into structured, compliant clinical SOAP notes, significantly reducing physician documentation time.   
For converting audio to text (transcribing audio), OpenAI's open source Speech Recognition model 'Whisper' (whisper-medium.en) has been used (along with Huggingface pipelines API). Also, the use of closed source 'gpt-4o-mini-transcribe' model has been shown (OpenAI API key needs to be purchased and included in the .env file, or added to Google Colab's 'secrets' field).  

Setup and Prerequisites:  
- Environment Setup: Clone the repository and install dependencies (pip install -r requirements.txt).
- Audio Data: Download a sample doctor-patient interaction audio file (e.g., from Kaggle or the PriMock57 dataset).
- Hugging Face Access: Create an account and generate an HF_TOKEN. Add this key to your .env file or Google Colab secrets.
- Llama 3.1 Access: Navigate to the model page (https://www.google.com/url?q=https%3A%2F%2Fhuggingface.co%2Fmeta-llama%2FMeta-Llama-3.1-8B) and agree to the terms and conditions to gain access to the weights.
- OpenAI API (Optional): If testing the gpt-4o-mini-transcribe model, purchase an API key and add it as OPENAI_API_KEY.

Key features:
1. Audio Transcription: Supports transcription via the Hugging Face Pipeline (using the openai/whisper-medium.en model) and the OpenAI API (gpt-4o-mini-transcribe).
2. Large Language Model (LLM): Employs the Meta-Llama/Llama-3.1-8B-Instruct model for generating minutes from the transcript.
3. Efficient Deployment: The LLM is loaded with 4-bit quantization using BitsAndBytesConfig and optimized for a T4 GPU runtime.
4. Structured Output: The model is prompted to generate a note following a common structure like SOAP (Subjective, Objective, Assessment, Plan):
   - (S)ubjective: The patient's chief complaint
   - (O)bjective: Vital signs, key physical exam findings, and critical lab/imaging results mentioned.
   - (A)ssessment: The final diagnosis or differential diagnoses discussed.
   - (P)lan: Medication changes, follow-up appointments, or lifestyle advice given.
