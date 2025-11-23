🚀 AI-Powered Research Assistant – Chrome Extension

An AI-driven Chrome Extension that helps users summarize selected text from any webpage and save research notes. Built with a Chrome Extension (Manifest V3) frontend and a Spring Boot AI backend.

✨ Features

AI Summary Generation — Select any text on a webpage and instantly get an AI-generated summary.

Two-Part System — Chrome Extension UI + Spring Boot backend for processing AI requests.

Persistent Notes — Save and load research notes using chrome.storage.local.

Real-Time Text Capture — Uses chrome.scripting to fetch highlighted webpage content.

Clean UI — Simple popup interface that displays summaries instantly.

📂 Project Structure
ai-research-assistant/
│
├── chrome-extension/
│   ├── manifest.json
│   ├── popup.html
│   ├── popup.js
│   ├── styles.css
│   ├── icons/
│   └── ...
│
└── backend/
    ├── src/main/java/... (Spring Boot code)
    ├── pom.xml
    └── application.properties

🧩 Chrome Extension (Frontend)
📌 How it Works

User selects text on any webpage.

The extension captures it using:

chrome.scripting.executeScript


Sends selected text to backend API.

Displays the AI summary inside popup.html.

Notes are saved locally using:

chrome.storage.local

⚙️ Backend (Spring Boot)
📌 Responsibilities

Receives text from the Chrome Extension

Sends it to the AI model for summarization

Returns summary back to the extension

Example Controller
@PostMapping("/api/research/process")
public ResponseEntity<String> process(@RequestBody ResearchRequest request) {
    return ResponseEntity.ok(aiService.processText(request.getContent(), request.getOperation()));
}

🛠️ Tech Stack
Frontend (Extension)

Chrome Extension API (Manifest V3)

JavaScript

HTML / CSS

Backend

Java

Spring Boot

WebClient / REST APIs

AI model (OpenAI / Gemini / Local model — depending on your setup)

🚀 How to Run the Project
1. Start the Backend
cd backend
mvn spring-boot:run


Backend runs at:

http://localhost:8080

2. Load Chrome Extension

Open Chrome → go to:

chrome://extensions/


Enable Developer Mode

Click Load Unpacked

Select the chrome-extension folder

📡 API Endpoint
Endpoint	Method	Description
/api/research/process	POST	Returns AI-generated summary

Request body:

{
  "content": "Selected text here",
  "operation": "summarize"
}

💡 Future Improvements

Add bullet-point summarization

Add translation and paraphrasing options

Add dark mode

Add “copy summary” button

Deploy backend to cloud (Render / Railway)

🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss your ideas.
