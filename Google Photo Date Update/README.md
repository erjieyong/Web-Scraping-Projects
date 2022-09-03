# Google Photos Date Update

## Background

This script is created for a specific use case to update whatsapp photos/videos uploaded to google photos.

Whenever we turn on google photos to automatically upload photos on to an existing folder, it will upload photos based on the system created date and time. On the other hand, whenever we factory reset our phone or change a new phone, whatsapp will download all the backup images and videos onto the new phone again, albeit with the downloaded date and time.

The problem exists when we get a new phone and turn on google photos automatic upload on a newly downloaded whatsapp folder of past images and videos. Google photos will upload all these images and videos and update it as the downloaded date although the actual photo shared date can be glean from the images and video file name.

Take for example the following whatsapp image:
- As of 1 January 2021, google photos was not turn on to automatically back up whatsapp images
- First received via whatsapp on 1 January 2021. The image file name would be saved as 'IMG-20210101-WA0001.jpg'
- Image was backed up by whatsapp to a cloud storage
- On 11 Aug 2022, new phone was purchased. Whatsapp was restored on new phone
- Image 'IMG-20210101-WA0001.jpg' was restored with creation date as 11 Aug 2022 <-- WRONG DATE
- Google photos was turn on to automatic back up whatsapp images
- Google photos upload 'IMG-20210101-WA0001.jpg' assuming it was taken on 11 Aug 2022

This script will update google photos of the correct date that the image or video is received based on the file name. For the above example, the correct date would be 1 January 2021

## Challenges

- Attempt was initially made to make use of google api to update the date of the backed up photos. However, this attempt was unsuccessful as google api does not allow updating of metadata on photos not originally uploaded via the API. Source: https://developers.google.com/photos/library/reference/rest/v1/mediaItems/patch"

- Attempt was made to use selenium to automatically open a browser instance, navigate to google photos and log in. However, this was not successful as google is strict on preventing user from loggin in using automated software such as selenium.
    - Note that this can be overcome using `undetected_chromedriver` package Source: https://github.com/ultrafunkamsterdam/undetected-chromedriver
    - As such, we arrived at the following script which require users to create a new instance of microsoft edge browser and then attaching selenium to the browswer in order to control it automatically. We are able to overcome the google authentication problem this way