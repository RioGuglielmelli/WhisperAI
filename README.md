
# WhisperAI (Whisp)

WhisperAI (Whisp for short) is a desktop-based voice assistant designed to enhance your Twitch streaming experience. It combines the power of OpenAI's GPT-4, Azure's neural voices, and seamless integration with OBS and Streamer.bot, providing a versatile tool for interacting with your audience in real-time.

## Table of Contents
- [Features](#features)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Integration with OBS and Streamer.bot](#integration-with-obs-and-streamerbot)
- [Project Structure](#project-structure)
- [Contributing](#contributing)

## Features
- **Voice Interaction**: Process user commands using GPT-4 and respond with Azure's neural TTS voices.
- **OBS Integration**: Control OBS scenes and overlays through the GUI or voice commands.
- **Streamer.bot Integration**: Send commands and interact with Streamer.bot directly from the GUI.
- **PyQt GUI**: A robust and modern desktop GUI built with PyQt for easy control and interaction.

## Installation

### Prerequisites
- Python 3.7+
- Pipenv for managing dependencies (optional)
- OBS WebSocket plugin installed and configured (for OBS integration)
- Streamer.bot set up and running (for command integration)

### Clone the Repository

\`\`\`bash
git clone https://github.com/RioGuglielmelli/WhisperAI.git
cd whisperAI
\`\`\`

### Install Dependencies

Using Pipenv:

\`\`\`bash
pipenv install
\`\`\`

If you are not using Pipenv, install dependencies manually:

\`\`\`bash
pip install -r requirements.txt
\`\`\`

## Configuration

### API Keys
Update the \`config.yaml\` file in the \`config/\` directory with your OpenAI API key and OBS WebSocket credentials.

\`\`\`yaml
openai_api_key: "YOUR_OPENAI_API_KEY"
obs_websocket:
  host: "localhost"
  port: 4444
  password: "your_obs_password"
\`\`\`

### OBS Setup
Ensure OBS is running with the WebSocket plugin enabled and configured according to your settings in \`config.yaml\`.

### Streamer.bot Setup
Configure Streamer.bot to receive commands from WhisperAI by setting up appropriate actions and WebSocket connections.

## Usage

### Running Whisp
Start the PyQt GUI by running \`whisp.py\`:

\`\`\`bash
python whisp.py
\`\`\`

The GUI will launch, allowing you to:

- Enter commands and send them to Streamer.bot.
- Control OBS scenes directly from the GUI.
- Interact with the voice assistant using GPT-4.

### Running the Flask Server (Optional)
If you are using Flask for handling external requests, start the Flask server with:

\`\`\`bash
python app.py
\`\`\`

This will enable external services to send commands to WhisperAI via HTTP requests.

## Integration with OBS and Streamer.bot

### OBS Integration
WhisperAI can interact with OBS via WebSocket to perform tasks such as:

- Changing scenes based on user commands.
- Triggering overlays or animations.

### Streamer.bot Integration
You can send commands to Streamer.bot directly from the Whisp GUI or via voice commands. This allows for real-time interaction with your Twitch chat and automated responses or actions.

## Project Structure

\`\`\`graphql
whisperAI/
│
├── app.py                  # Optional: Flask server entry point
├── whisp.py                # Main PyQt GUI application file
├── Pipfile                 # Pipenv dependencies file
├── Pipfile.lock            # Pipenv lock file
├── static/                 # Static files (CSS, JS) for Flask (if using Flask)
├── templates/              # HTML templates for Flask (if using Flask)
├── assistant/              # Logic for GPT-4, OBS, and Streamer.bot
│   ├── __init__.py         # Marks this directory as a Python package
│   ├── voice_assistant.py  # GPT-4 and Azure logic
│   ├── obs_controller.py   # WebSocket control for OBS
│   ├── streamer_bot.py     # HTTP requests to Streamer.bot
│   └── flask_routes.py     # Flask routes (if Flask is used for the API)
├── config/                 # Configuration files (API keys, etc.)
│   └── config.yaml         # Stores API keys and other config data
└── README.md               # Documentation about the project
\`\`\`

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request or open an issue if you have suggestions or find bugs.

### Steps to Contribute
1. Fork the repository.
2. Create a new branch (\`git checkout -b feature/your-feature\`).
3. Make your changes and commit them (\`git commit -am 'Add new feature'\`).
4. Push to the branch (\`git push origin feature/your-feature\`).
5. Open a Pull Request.
