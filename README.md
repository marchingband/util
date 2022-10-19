# util

arduino-esp32 does not support macos lower them 10.15 in the newer versions.  

The problem is /Users/${USER}/Library/Arduino15/packages/esp32/tools/esptool_py/{VERSION}/esptool. 
Download the file above into that location.  

the file here `esptool` is esptool.py, version 3.3.2, compiled on macos 10.13, for use with Arduino IDE, for arduino-esp32 v2.3 through 2.5  

You may also need to make the following change, if you get the error:
`exec: "python3": executable file not found in $PATH`

I confirmed that python3 is actually installed on my Mac by typing this in the Terminal, which gives the full path to it:

```
david$ which python3
/Library/Frameworks/Python.framework/Versions/3.8/bin/python3
```
Edit the platform.txt file in: /Users/david/Library/Arduino15/packages/esp32/hardware/esp32/2.0.5

Find the line:

`tools.gen_esp32part.cmd=python3 "{runtime.platform.path}/tools/gen_esp32part.py"`
Change python3 to the full path given in the "which python3" command earlier. In my case it becomes:

`tools.gen_esp32part.cmd=/Library/Frameworks/Python.framework/Versions/3.8/bin/python3 "{runtime.platform.path}/tools/gen_esp32part.py"`
Then everything worked fine!
