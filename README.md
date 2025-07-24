📧 Gmail AI Email Writer Extension
This Chrome Extension helps users generate professional email replies inside Gmail using Google Gemini AI. Just click one button, and an AI-generated reply is inserted automatically — saving time, increasing productivity, and helping with tone accuracy.

🚀 Features
✨ One-click AI-generated replies inside Gmail.

📩 Understands email context and crafts professional responses.

🔁 Seamless integration with Gmail UI.

🌐 Works with a local Spring Boot backend that connects to Gemini AI.

📁 Tech Stack
Layer	Technology
Frontend	Chrome Extension (HTML + JS)
Backend	Spring Boot (Java)
AI Engine	Gemini 2.0 Flash via API
Deployment	Localhost (for now)

🧩 Project Structure
bash
Copy
Edit
gmail-ai-email-writer/
│
├── manifest.json          # Extension metadata & config
├── content.js             # Injects button, reads email, sends API request
├── content.css            # Styles the "AI Reply" button
├── icons/                 # (Optional) Icon assets
│
└── spring-backend/        # Backend folder (not part of extension zip)
    ├── controller/
    ├── model/
    ├── service/
    ├── config/
    └── application.properties
🔧 How It Works
User opens Gmail

Extension script injects a custom "AI Reply" button near Gmail's reply box

On button click:

The email content is extracted from the page

A request is sent to the Spring Boot backend (localhost:8080/api/email/generate)

The backend forwards the content to the Gemini API

The AI-generated reply is returned and inserted into the Gmail reply box

📦 Setup Instructions
1. Clone & Set Up Backend
bash
Copy
Edit
cd spring-backend
Update application.properties:

properties
Copy
Edit
spring.application.name=email-writer-sb
gemini.api.url=https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent
gemini.api.key=YOUR_GEMINI_API_KEY
Run backend using IntelliJ or:

bash
Copy
Edit
./mvnw spring-boot:run
2. Load Chrome Extension
Open Chrome → chrome://extensions/

Enable Developer Mode

Click Load unpacked

Select the gmail-ai-email-writer/ folder

Go to Gmail and reload — the "AI Reply" button will appear

📸 Demo Screenshot
<img width="940" height="254" alt="image" src="https://github.com/user-attachments/assets/22480daa-34f4-4b75-ac53-8bac2ad3b511" />
<img width="940" height="254" alt="image" src="https://github.com/user-attachments/assets/0a455fa5-15e7-4c0c-8fb4-fedc350fb003" />
<img width="940" height="246" alt="image" src="https://github.com/user-attachments/assets/c0e03be7-5960-4f2f-9bcf-dae216caf973" />
<img width="497" height="258" alt="image" src="https://github.com/user-attachments/assets/cb1abd76-aa04-4762-907b-21c058568bed" />


🛠️ API Endpoint (Backend)
POST /api/email/generate

Request:

json
Copy
Edit
{
  "emailContent": "Hi, can you send me the report?",
  "tone": "professional"
}
Response:

json
Copy
Edit
{
  "generatedReply": "Hello, thank you for your message. I will share the report with you shortly."
}


🙋‍♂️ Author
Chetan Chaudhari
Backend + Frontend Developer | Chrome Extensions | AI Integration

📄 License
This project is for personal/educational use. Do not share your Gemini API key publicly.
