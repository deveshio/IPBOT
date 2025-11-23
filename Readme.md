# IPBOT

IPBOT automates a multi-step content workflow involving Pinterest and Instagram. It uses browser automation, credential handling, and generative AI to download, caption, and share images between platforms.

## Demo

Watch a full workflow demonstration here:<br>
[Video Demo](https://drive.google.com/file/d/1TCJU3GywoE5D4I3U4I4AS7jawYG06fBm/view)

## Features

- **Pinterest Automation:** Log in, navigate to a shared Idea board, find and download the top pin’s image.
- **Image Processing:** Renames the image and sends it with a (randomly, with variety) caption to the Gemini API for generative captioning to prevent spam/blocking.
- **Instagram Automation:** Log in, create a post, upload the image with the generated or prewritten caption, then log out.
- **Secure Credential Handling:** Reads credentials from `credentials.json`.
- **Full orchestration** via `run.sh` for one-touch operation.

## Project Workflow

1. **Start Process:** Run the included `run.sh` bash script.
2. **Open Browser:** Launches Firefox and navigates to Pinterest.
3. **Pinterest Actions:**
    - Log in using credentials from `credentials.json`.
    - Access the shared Idea board.
    - Retrieve and download the topmost pin image.
    - Log out and rename the image to its URL.
4. **Gemini API:** Sends the image to Gemini and chooses a caption (from 10 options, randomly) only if the returned random number matches, to avoid spam.
5. **Instagram Actions:**
    - Log in using credentials from `credentials.json`.
    - Create a post, upload the processed image, and sets the generated caption.
    - Log out and close Firefox.
6. **Caption Handling:** Maintains 10 prewritten captions (to prevent repetitive Gemini requests and blocking).
7. **Error Handling:** Logs errors and provides troubleshooting hints.

## Installation

1. **Clone the repo:**
   ```bash
   git clone https://github.com/deveshio/IPBOT.git
   cd IPBOT
   ```

2. **Install dependencies:**
   - Ensure Node.js, Bash, and Firefox are installed.
   - Install npm dependencies:
     ```bash
     npm install
     ```

3. **Prepare credentials:**
   - Create/modify `credentials.json` with your Pinterest and Instagram credentials:
     ```json
     {
       "pinterest": {
         "username": "your_pinterest_email",
         "password": "your_pinterest_password"
       },
       "instagram": {
         "username": "your_instagram_username",
         "password": "your_instagram_password"
       },
       "gemini": {
         "api_key": "your_gemini_api_key"
       }
     }
     ```

## Usage

Run the automation using:

```bash
bash run.sh
```

This script configures the environment, launches the browser, and starts the full image transfer and posting workflow.

### Advanced/ Further Work.

- **Configure Captions:** Edit your 10 captions in the appropriate script/config file.
- **Gemini API:** Ensure your API key and usage limits are set correctly and monitor for blocking.
- **Headless Browsing:** Optional configuration for headless browsers is possible, see the script’s comments.

## Troubleshooting

- **Browser Timeout:** Ensure Firefox is installed and accessible.
- **Credentials Fail:** Double-check format and fields in `credentials.json`.
- **Gemini Limitations:** If repeated captions cause blocking, adjust logic or cycle more captions.
- **Image Download Issues:** Check board sharing settings and Pinterest login steps.

## Contributing

**Open Source License**

This project is released as open source: anyone interested is free to fork, adapt, and use IPBOT for any purpose.

If you make general-purpose improvements, please open a pull request! I’m happy to check out your solution and if it’s broadly useful, I’ll merge it so everyone can benefit.

## License

This project uses the MIT License. See [LICENSE](LICENSE) for details.

---

© deveshio – For educational and automational purposes only.
