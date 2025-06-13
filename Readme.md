# Video Splitter & Telegram Uploader

A Flask-based web application that splits large video files into smaller parts and uploads them to Telegram, bypassing the 2GB file size limit.

![App Screenshot](https://via.placeholder.com/800x500.png?text=Video+Splitter+%26+Telegram+Uploader)

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
   git clone https://github.com/yourusername/video-splitter-telegram.git
   cd video-splitter-telegram