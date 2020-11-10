# CameraHub Tagger

Companion app for [CameraHub](https://github.com/djjudas21/camerahub) which writes EXIF tags to photos

This app will make use of CameraHub's RESTful API, which is still under development. Progress can be followed [here](https://github.com/djjudas21/camerahub/issues/5).

## Design

I anticipate the Tagger app will look and work in a similar way as [MusicBrainz Picard](https://picard.musicbrainz.org/).

The main window will have two panes. The left pane will list JPG files from the user's own system. The right hand pane will require the user to authenticate with CameraHub and will list the user's films and negatives, in the same way that Picard lists albums and tracks.

## Requirements

### Must

* Work on Linux, MacOS and Windows
* Support saved credentials
* Create new Scan records

### Should

* Show a diff of latent EXIF tags

### Could

* Support formats other than JPG
* Have some automated logic for matching JPGs to Scans

### Won't

* Upload JPGs to CameraHub

## Workflow

1. Start up, check for saved credentials and prompt for them if not
1. Left pane defaults to display contents of user's Photos directory for their OS
1. Right pane default to display list of user's films, which can be expanded to reveal negatives
1. Any JPGs which are already tagged with the uuid will get moved to the right hand side automatically, creating the Scan record if it doesn't already exist
1. The user will somehow associate JPGs with negatives. This needs discussion
1. JPGs that don't have a Scan uuid will have one generated, and the Tagger will create new Scan records in the API
1. Metadata for the Scan will be fetched from CameraHub
1. The user will save the changes to the files
