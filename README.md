# Sonic Pi via PulseAudio
A wrapper script making sonic-pi audible through PulseAudio

This script depends on the package 'pulseaudio-module-jack', sometimes
called 'pulseaudio-jack' (for example on Arch Linux or Alpine Linux).

This is a wrapper script around sonic-pi. All options passed to this script
will be passed on to sonic-pi. This script launches a dummy JACK server
and wires up sonic-pi's audio output to PulseAudio. This is supposed
to avoid common issues that arise from running JACK and PulseAudio
on the same sound card while also keeping the configuration effort minimal.
Additionaly, this allows to hear the sound of sonic-pi through any
bluetooth speaker or headset if they are set up to work with PulseAudio.

Keep in mind that routing sound through PulseAudio is an extra step
and that [PulseAudio resamples loopback devices.](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#module-loopback)
As more computing needs to be done,
audio issues can be possible depending on the hardware at hand.

On Arch Linux you can use the `PKGBUILD` to install this script to your system:
 - Click `Code` -> `Download ZIP`
 - Unpack the file and open a terminal in that directory
 - Run `makepkg --install`


The script is supposed to be POSIX compliant.


# FAQ
## I ran the script, sonic-pi started and is able to play scripts but there is no sound.
To verify that everything looks as it should:  
Launch `pavucontrol` and check that under the `Input Devices` tab there is an entry for `JACK to PulseAudio` and that under the `Playback` tab there is an entry for the Loopback from `JACK to PulseAudio`.  
Make sure that the drop-down `Show` at the bottom of the `pavucontrol` window is set to the `All *` option if the entries don't show up. Also make sure that the volumes are turned up if the entries are there and there is still no sound.

After that launch `qjackctl`, open the `Graph` window and make sure that the `JACK to PulseAudio` node is wired up to the same output pins of the `SuperCollider` node that are connected to the `playback` plugs of the `system` node. These are the ones from which `sonic-pi` will output its sound.  
If you don't want to install `qjackctl` you can also check that `jack_lsp -c` lists the following connections (the order is irrelevant and additional connections can be ignored):

```
system:playback_1
   SuperCollider:out_1
system:playback_2
   SuperCollider:out_2
SuperCollider:out_1
   system:playback_1
   JACK to PulseAudio:front-left
SuperCollider:out_2
   system:playback_2
   JACK to PulseAudio:front-right
JACK to PulseAudio:front-left
   SuperCollider:out_1
JACK to PulseAudio:front-right
   SuperCollider:out_2
```

If anything did not look as expected open an issue about it.
