##
## Programmer:    Benjamin Ory
## Syntax:        GNU Makefile
## Filename:      _includes/metadata/Makefile
##
## Description: Download metadata for the Mapping the Musical Renaissance from the Google Spreadsheet
##              for the project's metadata.  You need to update the SID variable below
##              when the deployment of the Google Apps Script has changed.
##
##              Type "make" in this directory to download the JSON files for the metadata.
##

MID = AKfycbw1m89jJvH1Y2CB7yE_AFafyQrEcOh01yX-n_j01SxndXscN_spyvkYwfkBdjzQiWqHVQ

all: download

download: data

data:
	curl -L "https://script.google.com/macros/s/$(MID)/exec?sheet=data" > data.json
