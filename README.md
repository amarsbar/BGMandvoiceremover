I'm making a haptics device for desktop. For it, I need to convert audio to haptics with ML since it would be too challenging to get support for each game.
Made an attempt at live audio separation using torchaudio and demucs. The idea is to remove the sounds of voices and music so that only the sounds of hitting remain for video games using a haptic device.
Can potentially be shared and used for PS5 controllers on PC. Users can experience haptic feedback for games that don't support it.
strikeseparation.ipynb works really well, and the results can be seen in before.mp3 and after.mp3.
The audio used in testing is from Elden Ring gameplay (not my gameplay footage!): 
https://www.youtube.com/watch?v=BPkNLt_iir8 

###For live audio separation:
What I've got so far can be seen in Audio Seperation.ipynb
It uses this to listen to windows audio: https://vb-audio.com/Cable/
Then processes that and sends it to the output device (cloud 2 headphones in demonstration.)
Delay so far is actually decent, but GPU usage is too high to be feasible for most games. Also, quality of noise removal is tragic!

You can find your device and the settings to use with this small chunk of code:

`import sounddevice as sd

devices = sd.query_devices()
for i, device in enumerate(devices):
    print(f"Device {i}:")
    print(f"   Name: {device['name']}")
    print(f"   Channels: {device['max_input_channels']} in, {device['max_output_channels']} out")
    print(f"   Sample Rate: {device['default_samplerate']} Hz\n")`
