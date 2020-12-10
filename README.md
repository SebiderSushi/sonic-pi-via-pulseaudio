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
