# ProcessedPiRecorder
A multiprocessed class of picamera for simplified deployment of high framerate computer vision on raspberry pi. 

Saves frames to a BigTif.

## Installation

      pip3 install ProcessedPiRecorder

## Requires

* tifffile        - 2019.7.26    
* picamera        - 1.13         
* opencv-contrib-python - 3.4.4.19     
* numpy           - 1.17.0  

## Basic Usage
You have to initialize the recorder and then tell it when to start recording. 
### Initialize:

While I do not use any positional arguments, I would recommend setting everything at initialization.

      from ProcessedPiRecorder import ProcessedPiRecorder as pcr

      myRecorder = pcr(tif_path='', x_resolution=0, y_resolution=0, scale_factor=1, framerate=0, 
                 rec_length=0, display=True, stereo=False, timestamp=False, reportHz=False,
                 monitor_qs= False, callback=None, cb_type=None, blocking=True,  write_tif=True,
                 tif_compression=6)
                                       
* tif_path - file to the output big tif file
* (x_resolution, y_resolution) - pixel dimensions to acquired by the sensor(s)
* scale_factor - sets the resize parameter at resolultion*scale_factor
* framerate - desired framerate in Hz
* rec_length - number of seconds to record
* display - if True, display video stream immediately prior to saving
* stereo - if True, hflip=True, stereo_mode='side-by-side', stereo_decimate=False
* timestamp - if True, all frames are timestapmed at aquisition
* report_Hz - if True, all frames have the current frame rate stamped at aquisition
* monitor_qs - if True, all frames have all queue lengths stamped at aquisition
* callback - if True, execute a callback function
* cb_type - if executing a callback, dictates if using the 2 process (='2Proc') or 3 process (='3Proc') workflow
* blocking - if True, block the main thread after spawning processes
* write_tif - if True, saves the video stream into tif_path
* tif_compression - specifies the degress of image compression used by tifffile

### Record

      myRecorder.recordVid()

## Contributors
This code was written and is maintained by [Matt Davenport](https://github.com/mattisabrat) (mdavenport@rockefeller.edu).
