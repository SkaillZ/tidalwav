# WAV Loop Editor for Unity

Edit .WAV file loop metadata in Unity.

Unity has limited support for looping metadata in .WAV files. It allows specifying
a loop start and end point which will be used when inside the loop (Audio will still
be played back from the start).

A very common use case is music with an intro that should be skipped after a loop,
which requires precise timing. 

Most other tools that support this functionality are either not widely available,
unmaintained or complicated to use, so this tool was created to allow editing
loops with a simple interface directly in Unity.

## Advantages

No custom scripts are needed with this method. All pre-processing is done in the editor to
create audio files that can be imported by Unity. The files can be played back with 
any standard AudioSource.

Compared to using scripts to set the playback position to the start of the loop
when the AudioClip's current time is past the loop's end, this method is framerate-independent, 
so there won't be any stutters.

## Installation

### Package Manager
Open the Package Manager in *Window - Package Manager*. Click the "+" button and choose
*Add package from git URL...*. Enter `https://github.com/SkaillZ/tidalwav.git` and click
*Add*.

### Manual Installation
Copy the files in the `Editor` folder into a subdirectory of the `Editor` folder
in your project.

## Usage

![Screenshot](doc/screenshot.png "Screenshot")

Open the WAV Loop Editor window in *Window - Audio - WAV Loop Editor*.
Next, select an AudioClip and click *Load*. Depending on the file size, loading might
take a while.

Click *Add Custom Loop* to add a loop to the file. You can select if you want to
display the start and end time in samples or minutes and seconds.
In the start and stop fields, you can enter the start and stop time of the loop
in the selected unit. Click *Save* to apply your changes to the file.

A preview window is displayed on the bottom. Click the "-" and "+" buttons to
zoom in and out and click the play button on the right to play back your loop.
You can also use the *Start* and *End* buttons to set the loop's start or end
point to the current playback position.

Please note that audio will still be played back from start to finish if looping is
disabled on the AudioSource. Only .WAV files are supported.

### Importing loops

Loading loops from other tools is supported. Since Unity only uses the first loop in the
WAV metadata, you can delete the other loops in a list to choose the one you want to use
if more than one loop is present.

## Known issues

* Loops in WAV files that were added in other programs might not show up correctly. 
* Finding a perfect start and end position is a little finicky due to the limitations
of Unity's AudioClip preview feature, so it's currently easier to find the exact start
and end position in an audio editing program like Audacity and enter them in the tool
manually.

## License

MIT
