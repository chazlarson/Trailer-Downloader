# Trailer-Downloader
Simple set of python scripts for downloading a movie trailer from Apple or from YouTube with help from TMDB. For quality purposes, the scripts will always attempt to download a trailer from Apple before falling back to TMDB and YouTube. This is useful if you are running a media server like Plex and you would like to have local trailers for each of your local movies.

## Requirements
-[Python 2.7+](https://www.python.org/)

-[tmdbsimple](https://github.com/celiao/tmdbsimple/blob/master/README.rst) + TMDB API Key

-[youtube-dl](https://github.com/rg3/youtube-dl/blob/master/README.md#installation)

-[ffmpeg](https://github.com/FFmpeg/FFmpeg)

-[tautulli](https://github.com/Tautulli/Tautulli) for automated downloading

## Installation
```
sudo -H pip install -r /path/to/scripts/requirements.txt
```

## Settings
Edit the **settings.ini** file. Here you can add your api key for TMDB, country code, language, resolution settings, path to your ffmpeg installation, and the path to your python installation.

## Usage

### Download Trailer For Specific Movie

To download a trailer for a specific movie, use the command below. You will need to provide the movie title, year, and directory or file to the script.
```
python /path/to/download.py --title "A Star Is Born" --year "2018" --directory "/path/to/movies/A Star Is Born (2018)"
```

This script can also be ran with an application like Tautulli to automatically download a trailer each time a new movie is added to Plex. To set this up, open Tautulli and go to Settings > Notification Agents and add a new notification agent. The type should be "script" and you'll want to add the path to the folder the scripts are located in and select download.py as your script in the configuration tab. Also add a name for the description. Next, go to the triggers tab and check the box for "Recently Added" and then go to the conditions tab and add a condition to only fire when "media type is movie". For the arguments tab, go to the "Recently Added" section and add the code below. After that, be sure to save it and you're all set.
```
<movie>--title "{title}" --year "{year}" --file "{file}"</movie>
```

### Download Trailers For All Movies In A Directory

To download trailers for an entire library that already exists, use the command below. You will need to supply the directory that all of your movie folders are in. The script will iterate through all of your movie folders in the directory and it will automatically pull the title and year from the folder name. Trailers will be downloaded into the folder for each movie.
```
python /path/to/download_all.py --directory "/path/to/movies"
```

This script expects your movies to be in a very specific structure. If your movies do not match the format below, you **will not** be able to use this script.

-Movies  
---Movie Title 1 (2014)  
-----Movie Title 1 (2014).mp4  
---Movie Title 2 (2009)  
-----Movie Title 2 (2009).mkv  

Enjoy!