# Asterisk Polly Playback

This project aims to implement an Asterisk dial plan application to download sounds synthesized by AWS Polly and save it inside a cache folder with gsm format.

Before performing the playback from a string provided by the user, check if the sound file already exists inside the cache folder.

If the cache file exists, it plays directly on the channel, using the same functionality as in the traditional playback application.

If there is no cached audio, the application connects directly to AWS Polly using curl to get sound in mp3/slin format and converting it to gsm format.

## TODO

- Implements curl to connect to AWS Polly
- Save and convert downloaded sound to gsm

## Config

Put into /etc/asterisk/polly.conf

```
[general]

cache_dir = /tmp
aws_access_key_id = your aws access key
aws_secret_access_key = your aws secret key
```

## Compiling

Add to your Asterisk apps/Makefile:

LIBS+= -lssl -lcrypto

## Running inside dialplan

same => n,pollyplayback(this is my first sound with polly)
