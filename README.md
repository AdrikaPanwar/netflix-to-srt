# netflix-to-srt
- [Get the subtitles](https://github.com/isaacbernat/netflix-to-srt#get-the-subtitles) from Netflix (`.xml` dfxp or `.vtt` files), YouTube or other sources.
- [Convert them](https://github.com/isaacbernat/netflix-to-srt#convert-them-into-srt) into `.srt` <br>

 > **Note:** There is a [video-tutorial covering all instructions step-by-step in Youtube on how to to download and convert subtitles from Netflix](https://www.youtube.com/watch?v=ZpejTczG8Ho) using Windows and Google Chrome.[![YouTube link to the tutorial](https://raw.githubusercontent.com/isaacbernat/netflix-to-srt/master/tutorial.png "YouTube link to the tutorial")](https://www.youtube.com/watch?v=ZpejTczG8Ho)


## Method 1
1. You need one of the following web browsers:
   - [Google Chrome](https://www.google.com/chrome/browser/desktop/)
   - Firefox
   - Safari
   - Microsoft Edge
   - Opera
2. Install [Tampermonkey](https://www.tampermonkey.net/), links below:
   - [Chrome extension](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo)
   - [Firefox addon](https://addons.mozilla.org/firefox/addon/tampermonkey/)
   - [Safari howto](https://www.tampermonkey.net/?browser=safari)
   - [Microsoft Edge addon](https://microsoftedge.microsoft.com/addons/detail/tampermonkey/iikmkjmpaadaobahmlepeloendndfphd)
   - [Opera addon](https://addons.opera.com/extensions/details/tampermonkey-beta/)
3. Install [Netflix - subtitle downloader](https://greasyfork.org/en/scripts/26654-netflix-subtitle-downloader) script for Tampermonkey.
4. To download the subtitles file from Netflix, open the episode in Netflix and download them by clicking on _"Download subs from this episode"_.
![netflix](https://github.com/user-attachments/assets/f08db7d7-c543-4661-9525-40f5406d298e)

## Method 2
You need [Google Chrome](https://www.google.com/chrome/browser/desktop/). *not tested on other web browsers*

1. Open devtools. This is usually accomplished by either:
    - Pressing `Cmd` + `Alt` + `i`.
    - Pressing `F12`.
2. Go to Network tab within dev tools.
3. Load your movie/episode.
4. Select the subtitle you want.
5. In devtools sort by name and look for a file with `?o=` at the beginning of the name (see image below).
![chrome](https://github.com/user-attachments/assets/b815a02a-fe51-48be-91d2-43feab6efb3d)

## Method 3
The information is extracted from [this post](http://forum.opensubtitles.org/viewtopic.php?t=15141).

You need FireFox and AdblockPlus Add-On. *not tested on other browsers*
- Start Netflix and your movie/episode (stream is active!)
- Start AdblockPlus, open blockable items
- Search: dfxp *(e.g. `>> #.nflximg.com/#/#/########.dfxp?v=1&e=#########&t=######_#####&random=1234567890`)*
- open the dfxp in a new window
- Save as

# YouTube-To-SRT
- Install [youtube-dl](https://github.com/ytdl-org/youtube-dl) (available for Windows, Mac and Linux)
- Download subs from the YouTube URL you like e.g. `youtube-dl --all-subs "https://www.youtube.com/watch?v=VHNfvFOBC0A"`
- Subtitles should be downloaded in the same folder were the command was ran. E.g. `NameOfTheVideo VHNfvFOBC0A.ca.vtt, NameOfTheVideo VHNfvFOBC0A.tlh.vtt`
- If you are missing a language, check that it's actually available. E.g. `youtube-dl --list-subs "https://www.youtube.com/watch?v=VHNfvFOBC0A"`
> **Note:** you can also use [youtube-dlp](https://github.com/yt-dlp/yt-dlp-wiki/blob/master/Installation.md) which is the fork version of [youtube-dl](https://github.com/ytdl-org/youtube-dl) by [Snap](https://snapcraft.io/yt-dlp)
 - Install [yt-dlp](https://github.com/yt-dlp/yt-dlp) using Snap:
 ```bash
 sudo snap install --edge yt-dlp
 ```
 - To download subtitles in SRT format from a YouTube URL, use:
 ```bash
  yt-dlp --skip-download --write-auto-subs --convert-subs srt --sub-lang "en" "https://youtu.be/cVsyJvxX48A" 
 ```
 This command downloads only the subtitles in SRT format.
 - If you want to download the subtitles in VTT format, you can use:
 ```bash
 yt-dlp --skip-download --write-auto-subs --sub-lang "en" "https://youtu.be/cVsyJvxX48A"
 ```
 - To download the video with audio and subtitles, simply omit the --skip-download option:
 ```bash
 yt-dlp --write-auto-subs --sub-lang "en" "https://youtu.be/cVsyJvxX48A"
 ```
> **Note:** If you don't enable subtitles in the YouTube video (captions), then the command will not work as expected. Make sure to enable subtitles before running the command.

## Clone Repo & Run Files
- [Get python](https://www.python.org/downloads/) (tested under python 2.7, 3.3 and newer). *If you have mac or linux you may skip this step*
- Clone this repository or [download it as a ZIP file](https://github.com/isaacbernat/netflix-to-srt/archive/refs/heads/master.zip) or [download `to_srt.py` file](https://raw.githubusercontent.com/isaacbernat/netflix-to-srt/master/to_srt.py)
- Run the script in the terminal (type `python to_srt.py` from the terminal on the folder you have `to_srt.py`)
  - Copy your subtitle files in the same directory as `to_srt.py`
    - Or use `-i INPUT_PATH` and `-o OUTPUT_PATH` for custom file locations
  - All `.xml` and `.vtt` files in the input directory will generate a converted `.srt` file on the output one
- Enjoy! (And **star the repo** if you liked it ;D)

## Why this repository?
VLC player could not reproduce that kind of xml subtitles and I could not find any tool that could easily transform the xml files to a suitable format (e.g. SubRip (`.srt`)) in Linux or Mac. I got a request for WebVTT (`.vtt`) and did the same.

## TODOs
- More robust file parsing than just some quick and dirty regexes.
- Javascript/web version so this can be done entirely through a browser.
- Real tests. The way to "test" it now is by running `python to_srt.py -i samples -o samples` from the the project's root directory and check the `.srt` results (or `python3 to_srt.py -i samples -o samples`).
- Create a pip package for this.
- More screenshots so 'Get the subtitles' section is easier to follow.

## Note:
In no way I am encouraging any kind of illegal activity. Please know your local laws and ask for written permissions from content owners (e.g. Netflix, YouTube) when necessary.

## Contribution 
Contributions are always welcome! Feel free to create a Pull Request and add screenshots for each step/method that works best for you. Your help will make this project even better for everyone.
