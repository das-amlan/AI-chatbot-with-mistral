# Mistral-7B Chatbot

This project implements a chatbot using the Mistral-7B-Instruct-v0.2 model.  It provides a user-friendly interface via Gradio to interact with the model.

![alt text](Home.png "chatbot-Home")

![alt text](q1.png "Question")

## Model Overview

The chatbot is built upon the Mistral-7B-Instruct-v0.2, a large language model (LLM) known for its instruction-following capabilities.  Mistral models are known for their strong performance across various NLP tasks, including text generation, question answering, and translation. This specific model has been fine-tuned for instruction following, making it particularly suitable for chatbot applications.

## Implementation Details

1. **Setup and Dependencies:** The project starts by installing necessary libraries: `transformers`, `torch`, `accelerate`, `bitsandbytes`, `sentencepiece`, `gradio`, and `PyPDF2`.  It then authenticates with the Hugging Face Hub to access the pre-trained model.

2. **Model Loading:** The `load_model` function downloads the Mistral-7B-Instruct-v0.2 model and its associated tokenizer.  Crucially, it uses 4-bit quantization (`load_in_4bit=True`) to reduce memory footprint and allow the model to run on consumer-grade GPUs. The `device_map="auto"` parameter allows the model to automatically determine the best device to load on.

3. **Prompt Formatting:** The `format_prompt` function takes the user's message and the chat history as input. It constructs a formatted prompt for the model. The format of the prompt is designed to provide context to the model, allowing it to maintain coherence in the conversation.

4. **Response Generation:** The `generate_response` function uses the formatted prompt to generate a response from the model. It uses parameters like `temperature` and `do_sample` to control the randomness and creativity of the generated text. The function is crucial for interfacing with the model and post-processing the output to isolate only the new response.  The generated response is then decoded using the tokenizer and cleaned up.

5. **Chatbot Function:** The `chat_response` function ties everything together.  It takes the user's message and chat history, generates a response using the model, and clears the GPU cache to prevent memory issues.

6. **Gradio Interface:** A Gradio interface provides an interactive chat experience. Users can type messages, and the chatbot will generate responses. Example prompts are included to help users get started. The `share=True` argument makes the Gradio app accessible via a public link.

## How to Run

1.  **Clone the repository:**
    ```bash
    git clone [your repository link]
    ```
2.  **Navigate to the project directory:**
    ```bash
    cd [your project directory]
    ```
3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt 
    ```
4.  **Log in to Hugging Face:**
    Run the script. The script will prompt you to log in to HuggingFace hub.
5.  **Run the application:**
    ```bash
    python your_script_name.py
    ```
This will launch the Gradio interface in your browser.

## Contributing

Contributions are welcome! Please feel free to open issues or submit pull requests.
