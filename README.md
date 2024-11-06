# Chordify:

#### Project Description:

The Chordify interface connects Hooke's Law theory with Spotify and YouTube, enabling users to explore a range of songs based on specific chord progressions. Once the user inputs the desired chord progression, the application fetches matching songs and adds them to a Spotify playlist. Additionally, it creates a YouTube playlist that lists tutorials for the songs with the specified chord progression for an instrument of the user's choice.

## Setup Instructions

### Step 1: Set Up a Virtual Environment

1. **Create a virtual environment**:

   ```
   python -m virtualenv venv
   ```

2. **Activate the virtual environment**:

   - On Windows:

     ```
     venv\Scripts\activate
     ```

3. **Install dependencies**:

   ```
   pip install -r requirements.txt
   ```

### Step 2: Prepare API Credentials

#### HookTheory API

1. Create a file in the project root directory containing your HookTheory credentials:

   ```
   Details.json
   ```

   ```
   {
     "username": "your_username",
     "password": "your_password"
   }
   ```

   This file will be used to retrieve the authorisation token needed to access HookTheory’s song data.

#### Spotify API

1. Obtain Spotify API credentials from the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/applications).

2. Create a file called

   ```
   spotify-keys.json
   ```

   in the project root directory with the following content:

   ```
   {
     "client_id": "your_client_id",
     "client_secret": "your_client_secret",
     "redirect_uri": "your_redirect_uri"
   }
   ```

   These credentials allow you to interact with the Spotify API.

#### YouTube API

To use the YouTube API, follow these steps:

1. **Create a Google Cloud Project**:
   - Go to the Google Cloud Console.
   - Click **Select a Project** > **New Project**.
   - Enter a **Project Name** and **Location**, then click **Create**.
2. **Enable the YouTube Data API**:
   - In the Google Cloud Console, go to **APIs & Services** > **Library**.
   - Search for **YouTube Data API v3**.
   - Select **YouTube Data API v3** and click **Enable**.
3. **Configure OAuth Consent Screen**:
   - Go to **APIs & Services** > **OAuth consent screen**.
   - Select **External** for user type, then click **Create**.
   - Fill out the required fields, such as **App Name** and **User Support Email** (your email).
   - Click **Save and Continue**. Under **Scopes**, add the `https://www.googleapis.com/auth/youtube.force-ssl` scope for full YouTube playlist management.
   - **Add Test Users**: Scroll down to the **Test Users** section. Add the email addresses of any accounts you want to grant access to this project, such as the account where you want the playlist to be created. This is required because the OAuth consent screen is in **Testing** mode, and only listed test users can access the API.
4. **Create OAuth Client Credentials**:
   - Go to **APIs & Services** > **Credentials**.
   - Click **Create Credentials** > **OAuth Client ID** and select **Web application** as the application type.
   - Name the client (e.g., "Web Client 1") and click **Create**.
   - Download the generated JSON file as `client_secret.json` and place it in the root directory of your project.

### Step 3: Authentication Tokens and API Usage

1. **Token Storage**:
   - The first time the script is run, you will be prompted to authenticate with each API via a web browser.
   - The YouTube API will store an access token in a file named `token.pickle` for future use.
2. **Running the Code**:
   - With your credentials in place, you can run the project code. Ensure the virtual environment is activated.

3. ## References

   - [HookTheory API documentation](https://www.hooktheory.com/api/trends/docs)
   - [Spotify API documentation](https://developer.spotify.com/documentation/web-api/)
   - [YouTube API documentation](https://developers.google.com/youtube/v3/docs/)

