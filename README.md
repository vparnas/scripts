# scripts

Helper utilities not yet deserving a separate repository

## circuits

Use to time exercise circuits with appropriate warm-up, transition, and break intervals, and emit a beep upon completion of each exercise. Helpful in a large-font terminal to display at a distance. For example, in *Awesome* window manager, I have a shortcut to invoke the *suckless* terminal in such a large-font mode (the -c parameter names the window class I can later use for custom window rules):

```
st -f 'Liberation Mono:pixelsize=36:antialias=false:autohint=false' -g '50x18' -c 'terminal_large'"
```

`circuits` uses the included `countdown` executable. Invoke `circuits -h` to display the command help.

Here are two sample circuits I've aliased in `~/.bashrc`:

```bash
alias circuits_abs='circuits -w 10 -d 45 -t 15 -b 30 -n 2 "High Knee Taps" "Russian twists" "Leg raises (6in off ground)" "Hip raises" "Scissor kicks" "Plank knees to elbow" "Chair sit-ups" "Seated in and outs" "Jumping Jacks"'

alias circuits_power='circuits -w 10 -d 15 -t 2 -b 30 -n 6 "Bicicle kicks" "Pushups" "Mountain climbers" "Squat boxing jumps" "Burpees" "Boxing hops"'
```

## jrnl_helpers

Provides useful helper functions for [jrnl](http://jrnl.sh), a universal plain-text journaling utility. The main expansion involves the three time-tracking and reporting functions:

+ jrnl_time_start: time track a task using an existing or a newly-entered time-tracking tag. Requires `dmenu`, available in most package managers. Displays the start notification using `notify-send`. 

+ jrnl_time_end: stop time tracking the current task. 

+ jrnl_report_time: with no parameters, report the total time for all time-tracked tags, including the grand total.

Configure parameters *TIME_TRACK_TAG* and *TIME_TRACK_JOURNAL* to use a different parent time-tracking tag (`@time-track` by default) and a different journal from than the default. You can also reconfigure these in an external `~/.jrnl_helpers.rc` file.

## record

Initiate an `ffmpeg` audio, video, or screencast recording using parameters `-a`, `-v`, or `-s`. Indicate the desired audio bitrate using `-b` (ex: `-b 128K`), the default being 224K. Pass an optional argument for the filename prefix (w/ optional directory), the defaults being "audio", "video", or "screencast" placed in the home directory. Invoke with `-h` to view the command line options. 

Uses *pulse* with the `libmp3lame` codec for the audio portion of each recording.

## killrecording

Terminate the recording initiated with *record*. Also helpful to assign to a shortcut key in a window manager.

## Others

+ audio_control: an interface to music player functions (pause, forward, back, etc). I also incorporated controls for the Spotify Linux client. 
+ countdown: displays a countdown for the specified interval in seconds. A friendlier version of the basic *sleep* command.
+ csv_to_markdown_table: Convert the STDIN supplied comma-separated table (with headings) to the simple markdown format. I assigned this to a VIM visual-mode mapping as such:

```vim
autocmd Filetype markdown,rmd vnoremap ,t :!~/scripts/csv_to_markdown_table<cr>
```

+ rsync-wrap: A wrapper for *rsync* using common parameters.
