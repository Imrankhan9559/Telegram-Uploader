# Video Splitter & Telegram Uploader

A Flask-based web application that splits large video files into smaller parts and uploads them to Telegram, bypassing the 2GB file size limit.

[App Screenshot]([https://via.placeholder.com/800x500.png?text=Video+Splitter+%26+Telegram+Uploader](https://raw.githubusercontent.com/Imrankhan9559/Telegram-Uploader/refs/heads/main/Assets/Screenshot%202025-06-14%20002115.png))

## Features

- **Large File Support**: Upload and process video files up to 100GB in size
- **Smart Splitting**: Automatically splits videos into 2GB parts using FFmpeg (no quality loss)
- **Telegram Integration**: Uploads split parts directly to your Telegram Saved Messages
- **Multiple Download Options**:
  - Download all parts as a single ZIP file
  - Download individual parts separately
- **Progress Tracking**: Real-time progress monitoring for both splitting and uploading
- **Session Management**: Automatic cleanup of temporary files
- **User-Friendly Interface**: Modern, responsive web interface

## How It Works

1. Upload your large video file (up to 100GB)
2. The server splits the file into 2GB parts using FFmpeg
3. You can then:
   - Download the parts to your computer
   - Upload all parts directly to your Telegram Saved Messages
4. Temporary files are automatically cleaned up after 1 hour

## Hosting Instructions

### Prerequisites

- Python 3.7+
- FFmpeg installed and in system PATH
- Telegram API credentials (API ID and API Hash)
- Linux/Windows server with sufficient storage space

### Installation

1. Clone the repository or download the source code:
   ```bash
   git clone https://github.com/Imrankhan9559/Telegram-Uploader
   cd Telegram-Uploader
   ```

2. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Create a `.env` file with your Telegram credentials:
   ```env
   API_ID=your_telegram_api_id
   API_HASH=your_telegram_api_hash
   FLASK_SECRET=your_random_secret_key
   ```

4. Install FFmpeg:

   On Ubuntu/Debian:
   ```bash
   sudo apt-get install ffmpeg
   ```

   On Windows: Download from FFmpeg official site

### Running the Application
```bash
python app.py
```
The application will be available at http://localhost:5000

### Production Deployment
For production, consider using:

- Gunicorn or Waitress as a WSGI server
- Nginx or Apache as a reverse proxy
- Supervisor or systemd for process management

Example with Gunicorn and Nginx:
```bash
gunicorn -w 4 -b 127.0.0.1:8000 app:app
```
Then configure Nginx to proxy requests to port 8000.

## Usage Guide

### Step 1: Access the Web Interface
Open your browser and navigate to http://your-server-address:5000

### Step 2: Upload Your Video
Click "Choose Video File" to select your file

Supported formats: MP4, AVI, MOV, MKV, WEBM

Max file size: 100GB

### Step 3: Monitor Processing
The app will show real-time progress:

- Upload progress (when transferring to server)
- Splitting progress (when creating parts)

### Step 4: Choose Action After Splitting

#### Download Options:
- "Download as ZIP" - Gets all parts in a single archive
- Individual download links for each part

#### Telegram Upload:
- Click "Upload to Telegram"
- First-time use requires Telegram authentication
- Files will appear in your Saved Messages

### Step 5: Cleanup (Automatic)
- Temporary files auto-delete after 1 hour
- Manual cleanup available via "Delete Files" button

## Technical Details

### File Storage Locations
- Uploads: `./uploads/`
- Split files: `~/Downloads/video_splitter/`
- Sessions: `./flask_session/`

### Telegram API Notes
- Uses Telethon library for uploads
- First run requires phone number verification
- Uploads use streaming to handle large files

## Troubleshooting

### Common Issues

#### FFmpeg not found:
- Ensure FFmpeg is installed and in PATH
- Verify with `ffmpeg -version`

#### Telegram authentication errors:
- Check `API_ID` and `API_HASH` in `.env`
- Delete `telegram_session` folder and retry

#### File size limits:
- Server must have enough disk space (2x file size recommended)
- Check available space with `df -h`

---

**Made by MysticMovies**  
Visit us at: [mysticmovies.site](http://mysticmovies.site)  
For support, Contact us on Telegram : [Imran Khan](https://t.me/@imrankhan95)

## License

This project is open-source under MIT License. Free to use and modify with attribution.

## Disclaimer

This tool is intended for legitimate use only. The developers are not responsible for any misuse of this software or violation of Telegram's Terms of Service.
