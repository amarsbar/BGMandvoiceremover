# Audio to Haptics: Background Music and Voice Removal

I'm making a haptics device for desktop. For it, I need to convert audio to haptics with ML since it would be too challenging to get support for each game.
Uses HDemucs and torchaudio to remove background music and voice sounds from video games. This cleanup allows the audio output to be sent to the haptic device to experience video game haptics without needing support.
Can potentially be shared and used for PS5 controllers on PC to gain audio-based haptic support which would otherwise be unavailable.

strikeseparation.ipynb works really well, and the results can be seen in before.mp3 and after.mp3.

The audio used in testing is from Elden Ring gameplay (not my gameplay footage!): 
https://www.youtube.com/watch?v=BPkNLt_iir8 

### For live audio separation:
What I've got so far can be seen in Live Audio Separation.ipynb

It uses this to listen to windows audio: https://vb-audio.com/Cable/

Then processes that and sends it to the output device.

You can find your device and the settings to use with this small chunk of code:

```
import sounddevice as sd

devices = sd.query_devices()
for i, device in enumerate(devices):
    print(f"Device {i}:")
    print(f"   Name: {device['name']}")
    print(f"   Channels: {device['max_input_channels']} in, {device['max_output_channels']} out")
    print(f"   Sample Rate: {device['default_samplerate']} Hz\n")
```

### Spectrogram Analysis

Comparing different versions of my realtime tracking modules to optimize continuity of output. Order descending in version (newer is lower).


![image](https://github.com/user-attachments/assets/19c3e7c6-11e6-43a6-8f17-5529e05bfe01)
![image](https://github.com/user-attachments/assets/5c4e93ef-919c-4bab-be54-7da43a51d3ad)


Optimal output:

![image](https://github.com/user-attachments/assets/98ff2a01-20ea-47fb-acab-b7757612b7cc)


