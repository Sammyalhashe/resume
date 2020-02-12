#

- With an addressable RGB LED strip, I built a music visualizer that takes sound input from two seperate sources:
  - A microphone
  - An android app that creates a websocket to communicate audio data
- The sound analysis is done on an Arduino with an ESP8266 Wifi chip and is written in C++.
  - The general algorithm is to keep a running average of the amplitudes of recorded volumes and also a running average of the "bump" in volume necessary to cause the lights to fire.
  - This is so the algorithm can adjust to songs that are naturally more quiet than others.
- I built an accompanying android app that periodically samples the audio data from the phone and transports it to the arduino through a websocket, quietly.
	- This android app also displays both the audio waveform and Fast-Fourier transform on the main activity.
- This project was made to decorate my appartment.
