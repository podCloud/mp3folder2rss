# mp3folder2rss

mp3folder2rss is a PHP script able to parse for medias the folder in which it is stored.

It generates a very simple basic RSS feed from the MP3 files contained in the same folder.
It parses ID3 tags to populate post data : title, author, description, link, pubdate, cover art.

That's about it. You put ONLY the rss.php file and the /.rss-dependencies/ folder in a folder with medias, BOOM, you have a podcast feed.
It's rough, it's kind of not for production use.

## What it does

- Auto-installs on first launch
- Creates a /.rss-dependencies/.cache folder to store all the things it will need.
- Parse the files in the folder and add posts for each media.
- Filter to only use podcasting files (audio/mp3, audio/m4a, video/mp4, video/m4v).
- Gets the pubDate from the file date of modification
- Gets info from the id3tags :
  - title from the title of the media (id3tag)
  - author from the artist of the media (id3tag)
  - description fom the comment section of the id3tags (no formatting)
  - link from the URL field of the media (id3tag)
  - artwork of each episode from the file (id3tag)
- Fallback when no title or description (uses the filename for the title)
- Fallback when no image for the episode (image of the feed)
- Uses PodShows XSLT stylesheet for an human readeable feed
- Other infos comes from .rss-dependencies/channel.config file

## Troubleshooting

Just delete the `/.rss-dependencies/.cache` folder, everything will reset.

## What is an ID3Tag ?

![ID3 Tag example](https://i.imgur.com/sLRo1WX.png)

ID3 Tags are metadata contained inside the MP3 audio file format.

It allows informations about the content to be stored in the file itself.
You can add the title, artist, album, track number, and the cover art for example.

To add id3tags to your files, we advise the following free softwares :

- [PodChapter](https://podchapter.bigaston.dev/) on Windows, Linux, or MacOS
  (can also add chapters to your file)
- [EasyTAG](https://wiki.gnome.org/Apps/EasyTAG) on Windows and Linux
- [MP3TAG](https://www.mp3tag.de/en/) on Windows and MacOS

(Media players such as iTunes are also able to edit those tags, FYI)

## Sources

The XSL template has been copied (and updated) from [https://github.com/TheCraigHewitt/Seriously-Simple-Podcasting](https://github.com/TheCraigHewitt/Seriously-Simple-Podcasting)
This project is a fork of [misnard/Podcast-rss-generator-from-folder](https://github.com/misnard/Podcast-rss-generator-from-folder).
