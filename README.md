## `playurl` – a console player launcher with URL handling

This script has been written mainly for piping purposes to be able to pass playable URLs to a player without switching to it. In can be used on the command line as well.
It doesn't play anything by itself but rather checks the passed URL and modifies it if needed, then creates a temporary playlist file and passes it the the selected player app/command.  
The script utilizes `yt-dlp` or `youtube-dl` to get audio streams URL from a passed YouTube video URL, thus allowing to play YouTube videos as audio-only using players that don't support YouTube URLs natively.
Local paths could be used instead of URLs.

## Dependencies
- **yt-dlp**  
  `apt install yt-dlp` to install on Debian GNU/Linux   
  `brew install yt-dlp` to install on macOS with Homebrew
- **jq**  
  `apt install jq`  
  `brew install jq`
- **curl**  
  `apt install curl` to install on Debian GNU/Linux  
  macOS ships with `curl` installed

Other tools and commands used in script which should be included in any default installation: `awk`, `basename`, `cp`, `date`, `file`, `grep`, `kill`, `killall`, `mkdir`, `nohup`, `pgrep`, `ps`, `sed`, `touch`, `tput`, `tr`, `wc`, `which`, `xargs`.

Supported players: IINA, MOC, mpv, mplayer, SMPlayer, VLC, nvlc. These can temporarely override the user-defined default player, which can be any player, not only the one from the list (it should be able to accept URLs as arguments).  
On macOS the script has been tested only with players installed with Homebrew. 

## Installation
No installation is needed. Just download it and make it the script executable:
```bash
wget https://raw.githubusercontent.com/kosivantsov/playurl/main/playurl
chmod +x playurl
```

For convenience, place it somewhere in your `$PATH`.

## Usage
```bash
Usage:
  playurl [PLAYER] [OPTIONS] [URL]

  This script plays media from a provided URL using a specified media player.
  YouTube videos are played as audio-only.
  YouTube playlists may take longer to parse as each video URL has to be resolved.

Options:
  PLAYER      Specify the media player to use (mvp, vlc, etc.)
              
  set PLAYER  Set PLAYER as the default player
  save        Save playlist with the specified URL to a file
  report      Print the name of the selected player
  help        Display this help message

Examples:
  playurl set mpv
           to set mpv as the default player
  playurl https://example.com/video
           to play the URL with the default player
  playurl vlc https://example.com/video
           to play the URL with vlc without setting it as the default player
```
