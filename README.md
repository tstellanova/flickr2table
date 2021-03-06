# Flickr2Table

##### Uses the REST APIs for Flickr and Airtable to pull new/updated photos daily from a Flickr album into searchable records in Airtable. 
This implementation looks at a "Flora" album of flowers & plants my girlfriend adds to every day as she identifies them on walks through San Francisco parks. It allows her to search and review the now 400+ species she's identified during the 2020 quarantine while in the field using the Airtable mobile app.  

#### Main Features:
  * Merges photos with the same title into a single record on Airtable, sorting those with tag 'Primary' as the first photo.
  * Parses a set of Flickr fields (incl. Title, Latitude, Longitude) into Airtable columns.
  * Parses the top line of the description field as the "Genus + Species" column.
  * Dynamically Parses any other lines in the description field containing a "=" by creating named columns to hold values provided.

#### Requirements:
  * Install requirements from the requirements.txt file using "pip install -r requirements.txt"
  * Create a config.py file with API keys and other info referenced in code.
  * Using the flickr_authenticate module here (or another using Oauth1), get an access token/secret pair for the Flickr account that owns the album of interest. 

#### Daily Process:
  * "python flickr_export.py --album_name Flora --window 1" creates .json file named with today's date in a flickr_exports folder.
  * "python airtable_upload.py --album_name Flora" parses and ingests this .json file to airtable.
  
## How photos appear on Flickr
Album View | Title and Description of a Single Photo
------------ | -------------
![Flickr album view.](README_flickr_album_view.png?raw=true?height=3 "Title") | ![Flickr title and description.](README_flickr_title_and_description.png?raw=true?height=3 "Title")

## And how they appear in Airtable
*filtered here to only "Native" flowers* 

![Airtable filtered view.](README_airtable_filtered.png?raw=true "Title")
![Airtable filtered view - continued.](README_airtable_filtered_cont.png?raw=true "Title")

### thank you to @josephbestjames for his [airtable module!](https://github.com/josephbestjames/airtable.py)
