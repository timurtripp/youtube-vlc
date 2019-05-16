# youtube-vlc

I couldn't find an easy way to open a YouTube video in VLC, in 1080p or 4K, without having to manually download it first. So I decided to write a simple and lightweight BASH script which would accomplish this, and work on my old 2006 iMac running OS X 10.8.5 as well as newer Macs or Linux machines.

youtube-vlc allows playback of 1080p or 4K YouTube videos in VLC at full quality using youtube-dl, much better than the 720p version you get when opening a YouTube URL through the VLC interface. VLC v3 is recommended to avoid playback issues present in v2. To keep the script lightweight, no metadata is passed to VLC except the video title.

youtube-vlc2 behaves the same but prioritizes MP4/M4A, which should help with avoiding the seeking/replay issues sometimes present in VLC, and achieve better playback performance on older hardware. The quality is usually capped at 1080p (may be 720p for some videos) because 4K is encoded as VP9 by YouTube, so this is equivalent to watching YouTube in Safari on a Mac.

youtube-qt and youtube-qta are bonus scripts for Mac users that allow YouTube playback in the built-in Quicktime Player. youtube-qt enables video playback, but this has a caveat, as the MAX quality for most YouTube videos will be the 720p version, due to the limitations of Quicktime Player and codecs used by YouTube (however, some livestreams may open in 1080p by default). youtube-qta enables playback of the audio only version (no video), which may be more useful in some cases given the 720p limitation of Quicktime playback.

Playback happens on-the-fly, no download is necessary. Any arguments passed to the script will be passed unchecked to youtube-dl, so the same options are avaliable. Be careful though, some arguments might break it, especially any that change the output.

youtube-dl download and readme can be found [here](https://github.com/ytdl-org/youtube-dl/blob/master/README.md).

### Compatibility

Because these are BASH scripts and youtube-dl is written in Python 2.6, the latest OS isn't necessary. The system requirements below take dependencies into account.

MacOS: Tiger 10.4.11 (Intel or PowerPC) or later and Python 2.6 or later and Quicktime 7 or later (youtube-qt), Lion 10.7.5 or later and VLC 3.0 or later (youtube-vlc and youtube-vlc2).

Linux: VLC 3.0 or later (youtube-vlc and youtube-vlc2).

The latest version of youtube-dl is required in all cases. Later versions of VLC 2 may be able to play some videos, but compatibility is not guarenteed.

### Installation

Place the scripts in the /usr/local/bin folder (you will need admin privileges to do this). You may need to run sudo chmod a+rx /usr/local/bin/youtube-* to ensure the scripts can be run. Afterward you can simply use them as commands in Terminal, same as you would with the normal youtube-dl.

### Usage

The most basic usage is simply the command followed by the URL of the YouTube video, this should result in the best quality avaliable:

    youtube-vlc https://www.youtube.com/watch?v=D1jojSZsoqo
    
More advanced options (such as selecting a lower video quality) are passed through to youtube-dl and work as well:

    youtube-vlc https://www.youtube.com/watch?v=D1jojSZsoqo -f best[height=720]
    
How about a playlist? Yes, that works as well:

    youtube-vlc https://www.youtube.com/playlist?list=PLFNI-pvvunispSSeNUUYgzkfe10R39J7a --playlist-start 1 --playlist-end 5
