# NotifyMePlease

NotifyMePlease is a Python-based application that automates the process of checking appointment availability on Aachen Auslanderbehorde website and sends notifications when appointments become available. It utilizes Selenium WebDriver for browser automation and can be scheduled to run at specified intervals.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Setup Instructions](#setup-instructions)
- [Configuring ChromeDriver](#configuring-chromedriver)
- [Configuration](#configuration)
- [Running the Script](#running-the-script)
- [Troubleshooting](#troubleshooting)
- [Dependencies](#dependencies)
- [License](#license)

## Prerequisites

Before setting up and running the application, ensure you have the following installed on your system:

- **Python 3.12**: You can download it from the [official website](https://www.python.org/downloads/).
- **Google Chrome Browser**: Download and install the latest version from [here](https://www.google.com/chrome/).
- **Git** (optional): For cloning the repository. Download from [here](https://git-scm.com/downloads).

## Setup Instructions

Follow these steps to set up the project environment:

1. **Clone the Repository**

   Clone the repository to your local machine using Git. If you don't have Git installed, you can download the repository as a ZIP file and extract it.

   ```bash
   git clone https://github.com/your-username/NotifyMePlease.git
   ```

   Navigate to the project directory:

   ```bash
   cd NotifyMePlease
   ```
2. **Create a Virtual Environment*

   It's recommended to use a virtual environment to manage project dependencies.

   ```bash
   python3.12 -m venv venv
   ```

   This will create a 'venv' directory in your project folder.
3. **Activate the Virtual Environment**

   - **Windows**:
     ```bash
     venv\Scripts\activate
     ```
   - **macOS and Linux:**
     ```bash
     source venv/bin/activate
     ```
   Once activated, your command prompt will be prefixed with `(venv)`.

4. **Install Dependencies**

   Install the required Python packages using `pip` and the provided `requirements.txt` file.
   ```bash
   pip install -r requirements.txt
   ```
## Configuring ChromeDriver

Selenium requires a WebDriver to interface with the chosen browser. In this case, we're using ChromeDriver for Google Chrome.

**Steps to Configure ChromeDriver:**
 1. **Check Your Chrome Version**
    - Open Google Chrome.
    - Click on the three-dot menu in the top-right corner.
    - Navigate to `Help` > `About Google Chrome`
    - Note down the version number (eg., `128.0.06613.84`)
2. **Download the Matching Chrome Driver**
   - Visit the [Chrome Driver Downloads](https://googlechromelabs.github.io/chrome-for-testing/)
   - Locate and download the ChromeDriver version that matches your Chrome browser version.
  
     For example, if your Chrome version is `128.0.06613.84`, download the corresponding ChromeDriver.
3. **Add ChromeDriver To Your Project**
   - Extract the downloaded ChromeDriver executable.
   - Place the `chromedriver.exe` file in project directory.
4. **Ensure ChromeDriver is Executable**
   On Windows, this step typically handled automatically.
   On macOs/Linux, you might need to make the driver executable:
   ```bash
   chmod +x path/to/chromedriver
   ```
## Configuration

The application uses a configuration file (`config.ini`) to manage settings such as URLs and webhook URLs. Ensure you have this file set up correctly.

**Example `config.ini`:**
```bash
[DEFAULT]
URL = https://termine.staedteregion-aachen.de/auslaenderamt/
NotificationType = discord  # or 'telegram'
WebhookURL = your_webhook_url 
TelegramBotToken = your_telegram_bot_token
TelegramChatID = your_telegram_chat_id
```
[How can i create a discord webhook url?](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks)

### Steps to Configure:
   Populate `config.ini` file with  the necessary configurations:
     - **URL:** The webpage to monitor for appointments.
     - **WebhookURL:** The endpoint to send notifications when an appointment is available.
     - **TelegramBotToken:** Put your telegram bok token here. I did not test the application with telegram bot.
     - **TelegramChatID:** I guess you know what to put here.
## Running the Script

Once the setup is complete, you can run the script to start monitoring for appointments.
  1. **Activate the Virtual Environment**
     Ensure your virtual environment is activated.
  2. **Run the Script**
     Execute the `main.py` script using Python3.12.
     ```bash
     python3.12 main.py
     ```
     The script will perform the following actions:
      - Launch google Chrome using Selenium WebDriver.
      - Navigate to the specified URL.
      - Accept cookies if prompted.
      - Navigate to the appointment section for RWTH Studenten.
      - Check for appointment availability.
      - Send a notification via the specified webhook if an appointment is found.
      - Log all actions and any errors encountered.
## Troubleshooting

If you encounter issues while running the script, consider following steps:

 1. **Ensure ChromeDriver Matches Chrome Version**

    - Verify that the ChromeDriver version matches your installed Chrome browser version.
    - Mismatched versions can cause errors like InvalidArgumentException or unexpected behavior.

 2. **Check WebDriver Configuration**

    Ensure that the path to chromedriver.exe is correctly specified in your script if you're not using WebDriver Manager.
    If using WebDriver Manager, ensure it's correctly configured to download and use the appropriate driver version.


 3. **Common Errors and Solutions**

    - selenium.common.exceptions.InvalidArgumentException:
        - Usually caused by incorrect or malformed URLs.
        - Ensure the URL in config.ini starts with http:// or https:// and is accessible.

    - Element Not Found Errors:
        - The script might be trying to interact with elements that have changed or are not present.
        - Update the element locators (e.g., XPath, ID) in your script to match the current webpage structure.

    - WebDriver Exceptions:
        - Ensure that ChromeDriver has the necessary permissions to execute.
        - On Windows, right-click the chromedriver.exe, go to Properties, and unblock it if necessary.
## Dependencies

All required Python packages are listed in the requirements.txt file. Key dependencies include:

    - Selenium: For browser automation.
    - WebDriver Manager: To manage browser drivers automatically.
    - Schedule: For scheduling periodic jobs.
    - Logging: For logging information and errors.
    
To install all dependencies, run:
```bash
pip install -r requirements.txt
```

## License
This project is licensed under the GNU General Public License.

## Contact 
twitchocean@gmail.com

   
   
