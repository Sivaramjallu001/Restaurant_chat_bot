# **BotMinds - AI-Powered Domain-Specific Chatbot**

BotMinds is an AI-powered chatbot built using advanced NLP techniques and fine-tuned LLMs (Large Language Models). This chatbot is designed to handle domain-specific conversations with contextual awareness, showcasing the potential of NLP and LLMs in real-world applications.

---

## **Key Features**
- **Domain-Specific Conversations**: Customizable for specific use cases like customer support, education, or programming.
- **Fine-Tuned LLM**: Utilizes a pre-trained **GPT-2** model fine-tuned with domain-specific conversational data.
- **Contextual Awareness**: Maintains context across conversations for coherent responses.
- **Multilingual Support**: Optional capability to handle multiple languages.
- **Real-Time Interactions**: Provides quick, responsive answers to user queries.

---

## **Technologies Used**
- **FastAPI**: For backend API development and webhook integration.
- **Hugging Face Transformers**: For fine-tuning and deploying GPT-based models.
- **MySQL**: For storing conversation history and chatbot metadata.
- **Pydantic**: For request validation and data serialization in FastAPI.
- **Python**: Primary language for backend and model training.
- Optional: **React** or **Streamlit** for creating a user-friendly chatbot interface.

---

## **Getting Started**

### **Prerequisites**
To run this project locally, you need:
- Python 3.8 or above
- MySQL installed and configured
- Basic understanding of NLP and LLM concepts

---

### **Installation**

1. **Clone the Repository**
   ```bash
   git clone https://github.com/Sivaramjallu001/BotMinds.git
   cd BotMinds
Set Up the Backend

Navigate to the backend folder:
bash
Copy
Edit
cd backend
Install required Python libraries:
bash
Copy
Edit
pip install -r requirements.txt
Set Up the MySQL Database

Create a database called botminds_db in MySQL.
Use the schema.sql file in the database directory to set up the required tables:
sql
Copy
Edit
CREATE DATABASE botminds_db;

USE botminds_db;

CREATE TABLE conversations (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_input TEXT NOT NULL,
    bot_response TEXT NOT NULL,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
Configure Environment Variables

Create a .env file in the backend folder and add the following variables:
makefile
Copy
Edit
DB_HOST=localhost
DB_USER=your_username
DB_PASSWORD=your_password
DB_NAME=botminds_db
Run the Backend Server

Start the FastAPI server:
bash
Copy
Edit
uvicorn main:app --reload
(Optional) Frontend Setup

If using a React-based frontend, navigate to the frontend directory and install dependencies:
bash
Copy
Edit
cd frontend
npm install
npm start
Access the Chatbot

Open your browser and go to http://localhost:8000/docs to explore the backend API or use http://localhost:3000 if a frontend is implemented.
How It Works
Users interact with the chatbot via the frontend or API endpoints.
The backend receives user input, processes it, and passes it to the fine-tuned GPT-2 model.
The model generates a response based on the user input and any contextual history.
The backend returns the response to the user and logs the conversation in the MySQL database.
Model Fine-Tuning
To fine-tune GPT-2:

Preprocess your domain-specific dataset into a text-based conversation format.

Fine-tune the model using Hugging Face’s Trainer API:

python
Copy
Edit
from transformers import GPT2Tokenizer, GPT2LMHeadModel, Trainer, TrainingArguments

tokenizer = GPT2Tokenizer.from_pretrained("gpt2")
model = GPT2LMHeadModel.from_pretrained("gpt2")

# Prepare your dataset here...

training_args = TrainingArguments(
    output_dir="./results",
    num_train_epochs=3,
    per_device_train_batch_size=8,
    save_steps=10_000,
    save_total_limit=2,
)

trainer = Trainer(
    model=model,
    args=training_args,
    train_dataset=train_dataset,
    eval_dataset=eval_dataset,
)

trainer.train()
model.save_pretrained("./fine_tuned_model")
Save and load the fine-tuned model in the backend for inference.

Contributions
Feel free to fork the repository, open issues, or submit pull requests. Contributions are always welcome!

Contact
Name: Sivaram Jallu
Email: jallusivaram@gmail.com
