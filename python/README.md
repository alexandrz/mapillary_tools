Python tools for Mapillary
=============


**add_fix_dates.py**

Script for adding dates to jpg files extracted from video with no tags. if you have a directory of files 
provide the directory, the datetime for the first file, and an increment in seconds. Ie if the photos are  
taken every 2 seconds  

    python add_fix_dates.py path-to-images/ '2014-11-27 13:01:01' 2


**add_mapillary_tag_from_exif.py**

Script for uploading images taken with other cameras than the Mapillary iOS or Android apps. 
Adds Mapillary data to EXIF tag to enable image to be handled in the same way as mapillary
native images.

    python add_mapillary_tag_from_exif path-to-images/ [sequence_id]

(Requires enviroment variables set: MAPILLARY_USERNAME, MAPILLARY_UPLOAD_TOKEN)

**add_project.py**

Writes the project tokens to the EXIF of images in the given path. This way, you can add photos to a project programmatically. Use like this:

    python add_project.py path-to-images/ project_name

(Requires enviroment variables set: MAPILLARY_USERNAME, MAPILLARY_PASSWORD)

**download_images.py**

Script to download images using the Mapillary image search API. Downloads images inside a rect (min_lat, max_lat, min_lon, max_lon).

    download_images.py min_lat max_lat min_lon max_lon [max_results]


**geotag_from_gpx.py**

A lightweight script for geotagging images with GPS data from a gpx file. Writes lat, lon, and bearing to the right EXIF tags. Use it like:

    python geotag_from_gpx.py path-to-images/ gpx_file [time_offset]

The time_offset is optional and is used if your camera clock is offset from your GPS clock.


**interpolate_direction.py**

Interpolates the direction of an image based on the coordinates stored in  
the EXIF tag of the next image in a set of consecutive images. 

    python interpolate_direction.py path-to-images/ [offset_angle]

**time_split.py**

This script organizes images into sequence groups based on a cutoff time. This is useful as a step before uploading lots of photos with the manual uploader. For example:

    python time_split.py path-to-images/ [cutoff_time]

If no cutoff time is given, it will be estimated based on the between-photo differences.


**upload.py**

This script uploads images taken with any of the Mapillary apps to the Mapillary backend. Just run:

    python upload.py path-to-images/ 


On Android Systems you can find the images under `/storage/emulated/0/Android/data/app.mapillary/files/mapillary/`.

On iOS, open iTunes, select your device, and scroll down to Mapillary under apps. You can see the files and copy them over from there.


**upload_each_folder_as_sequence.py**

Allows images in subfolders to be assigned unique sequence IDs.

    python upload_each_folder_as_sequence.py path-to-images/ 

(Requires enviroment variables set: MAPILLARY_USERNAME, MAPILLARY_PASSWORD)

**upload_with_authentication.py**

Script for uploading images taken with other cameras than the Mapillary apps. You need to set environment variables with your permission hashes, then you can upload as:

    python upload_with_authentication.py path-to-images/

(Requires enviroment variables set: MAPILLARY_USERNAME, 'MAPILLARY_PERMISSION_HASH', 'MAPILLARY_SIGNATURE_HASH)
from [upload hashes](http://api.mapillary.com/v1/u/uploadhashes)

See this [blog post](http://blog.mapillary.com/technology/2014/07/21/upload-scripts.html) for more details.

If upload fails mid-sequence due to connection failure or similar, you should manually push the images to the server by opening [Manual Uploads](http://www.mapillary.com/map/upload) and pressing "push to Mapillary".

