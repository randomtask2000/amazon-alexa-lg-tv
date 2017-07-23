# Amazon Alexa LG TV

Use your Echo or Echo Dot to turn on/off your LG Tv.

You need a TV with WebOS 3.

## Usage

- "Alexa, turn on TV"
- "Alexa, turn off the TV"

## Install

- Clone this repository
- Install python (I used 2.7.9 but should work with 3.x)
- Run "pip install -r requirements.txt"
- Update `alexa-tv.py` with your tv's MAC address
- Authenticate with "python lgtv.py auth [IP Address]"
- Start the script with `python alexa-tv.py`
- Enable "Mobile TV On"

When you try to turn on/off the TV for the first you will need to allow the script to access your TV. Alternatively, run "python lgtv.py auth [IP Address]"

### Supervisord

You can use supervisord to run your script
Sample config:

```
[program:alexa-tv]
command=/usr/bin/python /srv/amazon-alexa-lg-tv/alexa-tv.py
process_name=%(program_name)s
numprocs=1
directory=/srv/amazon-alexa-lg-tv/
autorestart=true
user=nobody                   ; setuid to this UNIX account to run the program
redirect_stderr=true
stdout_logfile=/var/log/alexa-tv.log
stdout_logfile_maxbytes=1MB
stdout_capture_maxbytes=1MB
environment=NODE_PATH="/usr/lib/nodejs:/usr/lib/node_modules:/usr/share/javascript"
```

## Thanks

- https://www.npmjs.com/package/lgtv
- https://github.com/toddmedema/echo


