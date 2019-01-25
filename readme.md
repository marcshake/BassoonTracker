# Bassoon Tracker

Browser based old-school Amiga Music Tracker in plain old javascript.

![Bassoon Tracker](./skin/bassoontracker_main.png?raw=true)

Plays and edits Amiga Mod files and FastTracker XM files.  
Live demo at [http://www.stef.be/bassoontracker/](http://www.stef.be/bassoontracker/)

If you have ever heard of [Protracker](https://en.wikipedia.org/wiki/Protracker) or [Fasttracker](https://en.wikipedia.org/wiki/FastTracker_2), then you know the drill,   
if not, then you are probably too young :-)

It needs a modern browser that supports WebAudio.
It's tested to work on Chrome, Firefox, Safari, Edge, Chrome on Android, mobile Safari and the Samsung Android Browser.
It works best in Chrome.

![Bassoon Tracker](./skin/bassoontracker_sampleeditor.png?raw=true)

**Features**
- Load, play, edit and save Protracker and FastTracker compatible module files  
- All Protracker audio effects are supported (99% accurate, in case of historical differences in playback engines, I tend to follow the Protracker 2.X one)
  - Portamento / Frequency slides (Effect 1, 2, 3, 5, E1 and E2)
  - Vibrato (Effect 4, 6 and E4)
  - Tremolo (Effect 7 and E7)
  - Arpeggio (Effect 0)
  - Glissando (Effect E3)
  - Sample offsets (Effect 9)
  - Volume slides and settings (effect A, C, E10 and E11)
  - Position jumps (effect B)
  - Pattern breaks, loops and delays (effect D, E6 and E14)
  - Speed settings (Effect F))
  - Sample Delay, Cut, Retrigger and Finetune (Effect E13, E12, E9 and E5)
  - Lowpass/LED filter (effect E0)
- Almost all FastTracker audio effects are supported
  - Volume and Panning Envelopes
  - Auto Vibrato
  - Multiple samples per instrument   
- Next to the tracker effects, there are per-channel effects for low, mid, high frequency, panning and reverb control
- Mute/solo tracks  
- Edit pattern data and sample properties  
- Up to 32 channels 
- Import 8bit WAV, 8SVX and RAW samples (as well as any other format AudioContext can read, like .mp3 and .ogg)
- Integrated sample editor: Edit and slice your samples right inside Bassoontracker
- Includes the historic ST-01 and ST-02 sample disks, released in 1987 (as well as a bunch of others)
- The [modarchive API](https://modarchive.org/) is integrated to access many thousands of music files
- The [modules.pl API](http://modules.pl/) is integrated to access even more music files
- Export to .mod, .xm, wav and .mp3
- Connect your Dropbox account to directly read and write your own files

The playback engine has gone through extensive compatibility testing, but as the Protracker code itself is somewhat messy and muddy
throughout different versions, there's always room for improvement.
If you find a module that doesn't sound the way it should, let me know!
There are still some very specific [Protracker 1 and 2 playback quirks](http://www.stef.be/bassoontracker/docs/trackerQuircks.txt) that are not implemented (and probably never will as they are too bat-shit-crazy)

**Missing features and bugs:**
 - no undo/redo functionality yet
 - the following FastTracker features are not fully supported yet
   - Tremor
   - "Set envelope position" command
   - PingPong Loops are unrolled to normal loops (There's no difference in sound but if you save your XM file, your samples will have changed.)
   - when writing XM files patterns are not packed so the resulting files will probably a little bigger then when saved with FastTracker.
 - Safari doesn't support WebAudio StereoPanners so songs will be played in mono on Safari.
 
Note: if you use an AZERTY, QWERTZ or DVORAK keyboard, you can set that option in the settings to have the correct layout when playing notes on your computer keyboard.

**How to Build**  
  - the build step is optional, there are no runtime dependencies (*bliss!*)  
  - just open dev.html in a browser to load the plain uncompressed scripts 
  - to build the packaged version:
    - run "npm i" to install the grunt build tools.
    - use "grunt" to build the compressed files -> index.html will be created.
    - use "grunt sprites" to build the spritesheet.
	  This will compact all files in the "skin/src" to a single .png file and will create a spritemap.

**Future plans**  
  - MIDI support!
  - undo/redo on pattern edits and sample edits
  - export and import .xi instruments
  - 3SM/Screamtracker file support, maybe Octamed too
  - Allow synth/FM instruments next to sample instruments.
  - Although the tracker concept is awesome - it also would be nice to integrate it in a more modern 
  "horizontal block compose" style interface where you can re-use and combine tracks/patterns in a 
  composition instead of endlessly copying tracks.
  - Allow multiple notes per track (or at least give the option to let them play when a new note is triggered)
  - More effects (echo, reverb, flange, ...) should probably be implemented with graphical track-envelopes instead of instrument envelopes or more numerical effect parameters.    All this would require (yet another) new file format, but that seems inevitable.
  - more simple HTML/CSS based layout - maybe the canvas approach is too heavy for really large screens? (this one is in progress)
  - plugins:
  	- Jukebox plugins, filter on genre/rating etc, hit play and let it perform.
  	- more expanded sample editor with audio processing features - probably as an external plugin
  	- Nibbles... we definitely need Nibbles.
  

**player**  
If you want to integrate the Bassoontracker playback routines in your own website, check out the "Standalone Player" examples in the "player"
or visit the (live demo)(http://www.stef.be/bassoontracker/player/)

