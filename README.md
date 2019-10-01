# ipad1-tvheadend-pi-tvhat
Project: repurpose the old Ipad 1st Gen as a TV viewer, thanks to Tvheadend and Pi TVHAT

**Limitations of Ipad 1st Gen**
- Ipad 1st Gen is stuck on iOS 5.1
- Poor CPU, that makes it laggy for any modern task
- It's a real pain to find and install suitable/available Apps for that iOS version.
- Default Video player app is really limited in term of video codecs and formats supported

**Good points of Ipad 1st Gen**
- Ipad's SoC has hardware decoder for H264 videos *(only Quicktime can benefit from it)*
- Quicktime player can play MPEG-TS stream encoded with H264 (video) + AAC (audio) up to FullHD
- a VLC version is available (software decoder only, work great with MPEG2, doesn't work with H264)
- Nice screen *(IPS, while limited resolution 1024x768 px)*


--> So basically it could be suitable to watch TV on Ipad1 for both TNT "SD" (MPEG2) with VLC or TNT "HD" (H264) with Quicktime internal player *(need to re-encode on-the-fly the sound from AC3 to AAC)*.

The Ipad 1st Gen would be the frontend/player, and the backend (aerial DVB-T TV receiver and streamer) would be done by [TVheadend](https://tvheadend.org/) on a Raspberry Pi equipped with [Pi TV HAT](https://www.raspberrypi.org/products/raspberry-pi-tv-hat/). *On-the-fly re-encoding of the sound from AC3 to AAC takes up to 20% CPU on the Raspi 2.*

Then an interface to select channels and lunch the stream to player is needed...

## Why a Web UI ?
- No exisitng or working native App for iOS 5.1 *(based on my searchs)*
- It's more flexible to develop for web frontend
- TVheadend has a good [Json API](https://github.com/dave-p/TVH-API-docs/wiki/API-Description)
- TVheadend can host some static files served by its webserver
- The old Safari browser supports Jquery up to version 1.12.4
- The old Safari browser does support "vlc://" URL scheme to send video url to VLC
- The old Safari browser support HTML5 Video element to send video url to Quicktime
