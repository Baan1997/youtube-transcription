youtube-transcription
=====================

Scripts to retrieve videos, upload them to YouTube, and retrieve the automatically-generated transcriptions. Requires you to first [register](https://developers.google.com/youtube/registering_an_application) a YouTube Data API-consuming application with Google.

## config.yaml

The scripts require a files called config.yaml (formatted like the included file config.yaml.example) containing your YouTube auth information. Note that if your YouTube account has two-factor authentication enabled, you'll have to [generate an application-specific password](http://support.google.com/accounts/bin/answer.py?hl=en&answer=185833), rather than providing your Google account's password.

## upload-videos.py

Accepts a json manifest with video URLs and metadata values. Retrieves the videos, uploads them to YouTube, and outputs a modified manifest including YouTube IDs.

Parameters:

* -i --input-file (required): the full path of the json manifest
* -o --output-file (optional): the full path of the modified manifest

If `-o` is not specified, the script will write the YT IDs to the input file.

## get-transcriptions.py

Accepts the modified manifest produced by upload-videos.py. Retrieves all transcripts associated with the videos and stores them in the supplied output directory.

Parameters:

* -i --input-file (required): the full path of the json manifest
* -o --output-dir (optional): the path of the directory in which to store the transcripts

`-o` defaults to `-`, which outputs transcription(s) to stdout.

## Format for input manifest (json):

```
{
"http://example.org/video.mp4": {
  "title": "Title",
  "category_term": "Film",
  "category_label": "Film &amp; Animation",
  "keywords": "some, useful, keywords",
  "description": "A nice description"
  }
}
```
