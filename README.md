### YT-DLP Video Downloader

A powerful video downloader tool built on top of yt-dlp with additional features for watermark removal and flexible configuration.

## Features

- Download videos from YouTube, Facebook, and many other platforms
- Preserve original video quality, audio, and resolution
- Remove static watermarks from videos using FFmpeg
- Configurable download profiles for different quality preferences
- Support for both Python and PowerShell environments
- Easy-to-use command-line interface


## Table of Contents

- [English](#english)

- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Watermark Removal](#watermark-removal)
- [Troubleshooting](#troubleshooting)



- [বাংলা](#বাংলা)

- [ইনস্টলেশন](#ইনস্টলেশন)
- [ব্যবহার পদ্ধতি](#ব্যবহার-পদ্ধতি)
- [কনফিগারেশন](#কনফিগারেশন)
- [ওয়াটারমার্ক অপসারণ](#ওয়াটারমার্ক-অপসারণ)
- [সমস্যা সমাধান](#সমস্যা-সমাধান)



- [License](#license)


---

# English

## Installation

### Prerequisites

- Python 3.9 or higher
- FFmpeg and FFprobe
- PowerShell 5.1 or higher (for Windows users)


### Setup Instructions

1. **Clone the repository**


```shellscript
git clone https://github.com/yourusername/yt-dlp-video-downloader.git
cd yt-dlp-video-downloader
```

2. **Install yt-dlp**


```shellscript
pip install yt-dlp
```

3. **Install FFmpeg**


For Windows (using winget):

```powershell
winget install Gyan.FFmpeg
```

For macOS (using Homebrew):

```shellscript
brew install ffmpeg
```

For Linux:

```shellscript
sudo apt update
sudo apt install ffmpeg
```

4. **Create downloads directory**


```shellscript
mkdir downloads
```

## Usage

### List Available Profiles

```powershell
# PowerShell
.\yt_dlp_downloader.ps1 -Command list-profiles
```

```shellscript
# Python
python yt_dlp_downloader.py list-profiles
```

### Download Videos

#### Download with Best Quality

```powershell
# PowerShell
.\yt_dlp_downloader.ps1 -Command download -Url "https://www.youtube.com/watch?v=dQw4w9WgXcQ" -Profile "best_quality"
```

```shellscript
# Python
python yt_dlp_downloader.py download "https://www.youtube.com/watch?v=dQw4w9WgXcQ" --profile best_quality
```

#### Download Facebook Videos/Reels

```powershell
# PowerShell
.\yt_dlp_downloader.ps1 -Command download -Url "https://www.facebook.com/watch?v=123456789" -Profile "best_quality"
```

```shellscript
# Python
python yt_dlp_downloader.py download "https://www.facebook.com/watch?v=123456789" --profile best_quality
```

#### Download Audio Only

```powershell
# PowerShell
.\yt_dlp_downloader.ps1 -Command download -Url "https://www.youtube.com/watch?v=dQw4w9WgXcQ" -Profile "audio_only"
```

```shellscript
# Python
python yt_dlp_downloader.py download "https://www.youtube.com/watch?v=dQw4w9WgXcQ" --profile audio_only
```

### Add New Profile

```powershell
# PowerShell
.\yt_dlp_downloader.ps1 -Command add-profile -ProfileName "720p" -Description "Download 720p video" -CommandOptions "--format bestvideo[height<=720]+bestaudio/best[height<=720] --merge-output-format mp4"
```

```shellscript
# Python
python yt_dlp_downloader.py add-profile "720p" "Download 720p video" "--format bestvideo[height<=720]+bestaudio/best[height<=720] --merge-output-format mp4"
```

## Configuration

The configuration is stored in `config.json`. Here's an example configuration:

```json
{
    "ffmpeg_path": "C:\\Program Files\\ffmpeg\\bin\\ffmpeg.exe",
    "ffprobe_path": "C:\\Program Files\\ffmpeg\\bin\\ffprobe.exe",
    "output_dir": "downloads",
    "output_template": "%(title)s [%(id)s].%(ext)s",
    "download_profiles": [
        {
            "name": "best_quality",
            "description": "Download best quality video and audio",
            "command": "--format bestvideo+bestaudio/best --merge-output-format mp4"
        },
        {
            "name": "audio_only",
            "description": "Extract audio only in mp3 format",
            "command": "-x --audio-format mp3 --audio-quality 0"
        },
        {
            "name": "preserve_all",
            "description": "Preserve original audio, resolution, and all attributes",
            "command": "--format bestvideo+bestaudio/best --merge-output-format mkv --no-mtime"
        }
    ]
}
```

### Setting FFmpeg Path

If FFmpeg is not in your system PATH, you need to specify the full path in the `config.json` file:

1. Find FFmpeg path using:

```powershell
where.exe ffmpeg
```


2. Update the `config.json` file with the correct paths.


## Watermark Removal

To remove watermarks from videos:

```powershell
# PowerShell
.\yt_dlp_downloader.ps1 -Command remove-watermark -VideoFile "downloads\video.mp4" -X 10 -Y 10 -Width 100 -Height 50
```

```shellscript
# Python
python yt_dlp_downloader.py remove-watermark "downloads/video.mp4" 10 10 100 50
```

Parameters:

- `X`: X-coordinate of the watermark (top-left corner)
- `Y`: Y-coordinate of the watermark (top-left corner)
- `Width`: Width of the watermark in pixels
- `Height`: Height of the watermark in pixels


## Troubleshooting

### FFmpeg Not Found

If you get an error about FFmpeg not being found:

1. Make sure FFmpeg is installed
2. Update the `ffmpeg_path` and `ffprobe_path` in `config.json` with the correct paths
3. Or add FFmpeg to your system PATH


### PowerShell Execution Policy

If you can't run the PowerShell script due to execution policy:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

### yt-dlp Updates

To update yt-dlp to the latest version:

```shellscript
pip install --upgrade yt-dlp
```

---

# বাংলা

## ইনস্টলেশন

### প্রয়োজনীয় সফটওয়্যার

- পাইথন ৩.৯ বা উচ্চতর সংস্করণ
- FFmpeg এবং FFprobe
- পাওয়ারশেল ৫.১ বা উচ্চতর সংস্করণ (উইন্ডোজ ব্যবহারকারীদের জন্য)


### সেটআপ নির্দেশাবলী

1. **রিপোজিটরি ক্লোন করুন**


```shellscript
git clone https://github.com/yourusername/yt-dlp-video-downloader.git
cd yt-dlp-video-downloader
```

2. **yt-dlp ইনস্টল করুন**


```shellscript
pip install yt-dlp
```

3. **FFmpeg ইনস্টল করুন**


উইন্ডোজের জন্য (winget ব্যবহার করে):

```powershell
winget install Gyan.FFmpeg
```

ম্যাকওএস এর জন্য (Homebrew ব্যবহার করে):

```shellscript
brew install ffmpeg
```

লিনাক্সের জন্য:

```shellscript
sudo apt update
sudo apt install ffmpeg
```

4. **ডাউনলোড ডিরেক্টরি তৈরি করুন**


```shellscript
mkdir downloads
```

## ব্যবহার পদ্ধতি

### উপলব্ধ প্রোফাইল দেখুন

```powershell
# পাওয়ারশেল
.\yt_dlp_downloader.ps1 -Command list-profiles
```

```shellscript
# পাইথন
python yt_dlp_downloader.py list-profiles
```

### ভিডিও ডাউনলোড করুন

#### সর্বোচ্চ মানের ভিডিও ডাউনলোড করুন

```powershell
# পাওয়ারশেল
.\yt_dlp_downloader.ps1 -Command download -Url "https://www.youtube.com/watch?v=dQw4w9WgXcQ" -Profile "best_quality"
```

```shellscript
# পাইথন
python yt_dlp_downloader.py download "https://www.youtube.com/watch?v=dQw4w9WgXcQ" --profile best_quality
```

#### ফেসবুক ভিডিও/রিলস ডাউনলোড করুন

```powershell
# পাওয়ারশেল
.\yt_dlp_downloader.ps1 -Command download -Url "https://www.facebook.com/watch?v=123456789" -Profile "best_quality"
```

```shellscript
# পাইথন
python yt_dlp_downloader.py download "https://www.facebook.com/watch?v=123456789" --profile best_quality
```

#### শুধুমাত্র অডিও ডাউনলোড করুন

```powershell
# পাওয়ারশেল
.\yt_dlp_downloader.ps1 -Command download -Url "https://www.youtube.com/watch?v=dQw4w9WgXcQ" -Profile "audio_only"
```

```shellscript
# পাইথন
python yt_dlp_downloader.py download "https://www.youtube.com/watch?v=dQw4w9WgXcQ" --profile audio_only
```

### নতুন প্রোফাইল যোগ করুন

```powershell
# পাওয়ারশেল
.\yt_dlp_downloader.ps1 -Command add-profile -ProfileName "720p" -Description "Download 720p video" -CommandOptions "--format bestvideo[height<=720]+bestaudio/best[height<=720] --merge-output-format mp4"
```

```shellscript
# পাইথন
python yt_dlp_downloader.py add-profile "720p" "Download 720p video" "--format bestvideo[height<=720]+bestaudio/best[height<=720] --merge-output-format mp4"
```

## কনফিগারেশন

কনফিগারেশন `config.json` ফাইলে সংরক্ষিত থাকে। এখানে একটি উদাহরণ কনফিগারেশন দেওয়া হল:

```json
{
    "ffmpeg_path": "C:\\Program Files\\ffmpeg\\bin\\ffmpeg.exe",
    "ffprobe_path": "C:\\Program Files\\ffmpeg\\bin\\ffprobe.exe",
    "output_dir": "downloads",
    "output_template": "%(title)s [%(id)s].%(ext)s",
    "download_profiles": [
        {
            "name": "best_quality",
            "description": "Download best quality video and audio",
            "command": "--format bestvideo+bestaudio/best --merge-output-format mp4"
        },
        {
            "name": "audio_only",
            "description": "Extract audio only in mp3 format",
            "command": "-x --audio-format mp3 --audio-quality 0"
        },
        {
            "name": "preserve_all",
            "description": "Preserve original audio, resolution, and all attributes",
            "command": "--format bestvideo+bestaudio/best --merge-output-format mkv --no-mtime"
        }
    ]
}
```

### FFmpeg পাথ সেট করা

যদি FFmpeg আপনার সিস্টেম পাথে না থাকে, তাহলে `config.json` ফাইলে পূর্ণ পাথ উল্লেখ করতে হবে:

1. FFmpeg পাথ খুঁজুন:

```powershell
where.exe ffmpeg
```


2. `config.json` ফাইলে সঠিক পাথ আপডেট করুন।


## ওয়াটারমার্ক অপসারণ

ভিডিও থেকে ওয়াটারমার্ক অপসারণ করতে:

```powershell
# পাওয়ারশেল
.\yt_dlp_downloader.ps1 -Command remove-watermark -VideoFile "downloads\video.mp4" -X 10 -Y 10 -Width 100 -Height 50
```

```shellscript
# পাইথন
python yt_dlp_downloader.py remove-watermark "downloads/video.mp4" 10 10 100 50
```

প্যারামিটার:

- `X`: ওয়াটারমার্কের X-অবস্থান (উপরের-বাম কোণ)
- `Y`: ওয়াটারমার্কের Y-অবস্থান (উপরের-বাম কোণ)
- `Width`: ওয়াটারমার্কের প্রস্থ (পিক্সেলে)
- `Height`: ওয়াটারমার্কের উচ্চতা (পিক্সেলে)


## সমস্যা সমাধান

### FFmpeg পাওয়া যাচ্ছে না

যদি FFmpeg সম্পর্কে এরর পান:

1. নিশ্চিত করুন যে FFmpeg ইনস্টল করা আছে
2. `config.json` ফাইলে `ffmpeg_path` এবং `ffprobe_path` সঠিক পাথ দিয়ে আপডেট করুন
3. অথবা FFmpeg কে আপনার সিস্টেম পাথে যোগ করুন


### পাওয়ারশেল এক্সিকিউশন পলিসি

যদি এক্সিকিউশন পলিসির কারণে পাওয়ারশেল স্ক্রিপ্ট চালাতে না পারেন:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

### yt-dlp আপডেট

yt-dlp কে সর্বশেষ সংস্করণে আপডেট করতে:

```shellscript
pip install --upgrade yt-dlp
```

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [yt-dlp](https://github.com/yt-dlp/yt-dlp) for the amazing video downloading capabilities
- [FFmpeg](https://ffmpeg.org/) for video processing functionality


---

**Note**: This project is for educational purposes only. Please respect copyright laws and terms of service of the websites you download content from.
