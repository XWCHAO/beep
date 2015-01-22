beep
====

A Go program that is useful for alerting the end of a long running command execution.
Beep can also play piano music sheet with optional voices. To play a demo music, run:<br>

```$ beep -p | beep -m```<br>

[Play demo&nbsp; ▶](http://angiud.com/beep/demo-mozart-k33b.mp3)<br>
[Play demo with piano voice&nbsp; ▶](http://angiud.com/beep/demo-mozart-k33b-piano.mp3)
Compiling
=========
```
On Linux:
 $ apt-get install golang libasound2-dev  # for Debian and Ubuntu
 $ git clone http://github.com/dbatbold/beep
 $ cd beep
 $ go build
 $ strip beep  # optional
 $ cp beep /usr/bin/  # as root

On Windows: (requires MinGW, Go compiler from golang.org)
 C:\> cd beep
 C:\beep> build.bat
 C:\beep> copy beep.exe \windows\system32
```
Prebuilt binaries
===============
 Windows: [beep.exe](http://angiud.com/beep/binary/windows/beep.exe) &nbsp; ```MD5: 75ebded6bb69a297f072a63c4add4a3c```<br>
 Linux 64-bit: [beep](http://angiud.com/beep/binary/linux/beep) &nbsp; ```MD5: 01f120dd36c0d76e89942a1775f82520```
Usage
=====
```
beep [options]
  -c=1: beep count
  -d="default": audio device, Linux example: hw:0,0
  -f=523.25: frequency in Hertz (1-22050)
  -h: print help
  -l: beep per line from stdin
  -m: play music notes from stdin (see beep notation)
  -p: print the demo music by Mozart
  -t=1: beep time duration in millisecond (1-60000)
  -v=100: volume (1-100)
  -b: send bell to PC speaker
  -q: quiet stdout while playing music
  -n: print notes while playing music
  -o=file: output music waveform to a WAV file. Use '-' for stdout
```
Beep notation
=============
```
Piano key map:
  | | | | | | | | | | | | | | | | | | | | | | 
  |2|3| |5|6|7| |9|0| |=|a|s| |f|g| |j|k|l| |
 | | | | | | | | | | | | | | | | | | | | | | 
 |q|w|e|r|t|y|u|i|o|p|[|]|z|x|c|v|b|n|m|,|.|

 q - middle C (261.6 hertz)

 Left and right hand keys are same. Uppercase 
 letters are control keys. Lowercase letters
 are music notes. Space bar is current duration
 rest. Spaces after first space are ignored.
 Lines start with '#' are ignored.


Control keys:

 Rest:
 RW     - whole rest
 RH     - half rest
 RQ     - quarter rest
 RE     - eighth rest
 RS     - sixteenth rest
 RT     - thirty-second rest
 RI     - sixty-fourth rest

 Durations:
 DW     - whole note
 DH     - half note
 DQ     - quarter note
 DE     - eighth note
 DS     - sixteenth note
 DT     - thirty-second note
 DI     - sixty-fourth note

 Octave:
 H0     - octave 0 keys
 HL     - octave 1, 2, 3 (left hand keys)
 HR     - octave 4, 5, 6 (right hand keys)
 H7     - octave 7, 8 keys

 Tempo:
 T#     - where # is 0-9, default is 4

 Sustain:
 SA#    - attack time, where # is 0-9, default is 6
 SD#    - decay time, 0-9, default 7
 SS#    - sustain level, 0-9, default 7
 SR#    - release time, 0-9, default 8

 Voice:
 VD     - Computer generated default voice
 VP     - Piano voice
 VV     - Violin voice (WIP)
 VN     - If a line ends with 'VN', the next line will be played 
          harmony with the line.

 Chord:
 C#     - Play next # notes as a chord, where # is 2-9. 
          For example C major chord is "C3qet"

 Amplitude:
 A#     - Changes current amplitude, where # is 1-9, default is 9

 Measures:
 |      - bar, ignored
 ' '    - space, ignored
 Tab    - tab, ignored
```
Demo Music
==========
```
# Mozart K33b
VP SA8 SR9
A9HRDE cc DScszs|DEc DQzDE[|cc DScszs|DEc DQz DE[|vv DSvcsc|DEvs ]v|cc DScszs|VN
A3HLDE [n z,    |cHRq HLz, |[n z,    |cHRq HLz,  |sl z,    |]m   pb|z, ]m    |

A9HRDE cz [c|ss DSsz]z|DEs] ps|DSsz][ z][p|DEpDQ[ [ || DERE] DS][p[ |VN
A3HLDE [n ov|]m [n    |  pb ic|  n,   lHRq|HLnc DQ[ || DEcHRq HLvHRw|

A9HRDS ][p[ ][p[|DE] DQp DEi|REc DScszs|cszs |cszs|DEcDQzDE[|REv DSvcsc|DEvs ]v|VN
A3HLDE bHRe HLvw|cHRq   HLic|[n  ]m    |z,   |]m  |zn   z,  |sl  [,    |z. DQp |

A9HRDE REc DScszs|DEcz [c|REs DSsz]z|DEs] ps|DSsz][ z][p|DE[DSitDQr|VN
A3HLDE z,  ]m    |[n   ov|]m  [n    |pb   ic|nz     sc  |DQn      [|
```
[Play with default voice&nbsp; ▶](http://angiud.com/beep/demo-mozart-k33b.mp3)<br>
[Play with natural piano voice&nbsp; ▶](http://angiud.com/beep/demo-mozart-k33b-piano.mp3)
Natural Voices
==============

Beep uses computer generated voices, if there are no voice files exist.
A voice file is a ZIP file contains sound samples of all notes that the
music instrument can play. By downloading and placing voice files to
specific locations where beep find will improve sound quality.

**Voice files:**<br>
 Piano voice: [piano.zip](http://angiud.com/beep/voices/piano.zip) (13MB)<br>
 Violin voice: [violin.zip](http://angiud.com/beep/voices/piano.zip) (6.9MB)<br>

**Voice file location:**<br>
 Windows: ```C:\Users\{username}\_beep\voices\``` <br>
 Windows XP: ```C:\Documents and Settings\{username}\_beep\voices\``` <br>
 Linux: ```/home/{username}/.beep/voices/```

Currently the violin voice has not been tested with a music sheet.
Usage Examples
==============
```
 $ cp -vr directory target; beep
 $ ffmpeg -i video.mp4 -vn -acodec libmp3lame sound.mp3; beep -t 3000
 
 # use '&' symbol instead of ';' on Windows
 C:\>dir /s \windows\*.cpl & beep
 
 # alarm for download completion
 $ curl -O http://host.com/bigfile.tgz; beep -c 4 -f 1000
 
 # beep for every text file found under home
 $ find ~ -name '*.txt' | beep -l
 
 # set an alarm for 1 hour from now
 $ sh -c 'sleep 3600; beep -t 300 -c 6' &
 
 # play all piano notes
 $ echo "DEH0,l.\
         HLq2w3er5t6y7ui9o0p[=]azsxcfvgbnjmk,l.\
         HRq2w3er5t6y7ui9o0p[=]azsxcfvgbnjmk,l.\
         H7q2w3er5t6y7ui" | beep -m
 
 # play Mozart K33b
 $ beep -p | beep -m
 C:\>beep -p | beep -m
 
 # dump music waveform to a WAV file
 $ beep -p | beep -m -o music.wav
 
 # pipe to MP3 encoder
 $ beep -p | beep -m -o - | lame - music.mp3
 
 # play misic sheet from a file
 $ beep -m < sheet.txt
 C:\>beep -m < sheet.txt

 # generate 528Hz sine wave for 60 seconds (wine glass frequency)
 $ beep -f 528 -t 60000
 
 # middle C note
 $ beep -f 261.625565 -t 1500
```
