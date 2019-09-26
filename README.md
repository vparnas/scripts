# scripts

Helper utilities not yet deserving a separate repository

## circuits

Use to time exercise circuits with appropriate warm-up, transition, and break intervals, and emit a beep upon completion of each exercise. Helpful in a large-font terminal to display at a distance. For example, in *Awesome* window manager, I have a shortcut to invoke the *suckless* terminal in such a large-font mode (the -c parameter names the window class I can later use for custom window rules):

```
st -f 'Liberation Mono:pixelsize=36:antialias=false:autohint=false' -g '50x18' -c 'terminal_large'"
```

`circuits` uses the included `countdown` executable. Invoke `circuits -h` to display the command help.

Here are two sample circuits I've aliased:

```bash
alias circuits_abs='circuits -w 10 -d 45 -t 15 -b 30 -n 2 "High Knee Taps" "Russian twists" "Leg raises (6in off ground)" "Hip raises" "Scissor kicks" "Plank knees to elbow" "Chair sit-ups" "Seated in and outs" "Jumping Jacks"'

alias circuits_power='circuits -w 10 -d 15 -t 2 -b 30 -n 6 "Bicicle kicks" "Pushups" "Mountain climbers" "Squat boxing jumps" "Burpees" "Boxing hops"'
```

## copy-cmd-output

Using *dmenu* or *slmenu*, depending on your environment, display the commands and their outputs visible in your terminal window, enabling you to copy the one chosen.

## edit-stdin

Using a terminal emulator or a new *tmux* window, depending on your setup, open the terminal buffer contents in the configured text editor.

## linkgrabber

Using *dmenu* or *slmenu*, depending on your environment, display all links visible in the terminal buffer, and select one to copy.

## minhttpserver

An experimental bash http server using *nc* (netcat). Serves `index.html` by default, or any specifically requested document. Supports GET, GET with querystring, as well as POST methods.

## record

Initiate an `ffmpeg` audio, video, or screencast recording using parameters `-a`, `-v`, or `-s`. Indicate the desired audio bitrate using `-b` (ex: `-b 128K`), the default being 224K. Pass an optional argument for the filename prefix (w/ optional directory), the defaults being "audio", "video", or "screencast" placed in the home directory. Invoke with `-h` to view the command line options. 

Uses *pulse* with the `libmp3lame` codec for the audio portion of each recording.

## killrecording

Terminate the recording initiated with *record*. Also helpful to assign to a shortcut key in a window manager.

## tabletocsv

Accepts a web page source via standard input, extracts the first table, and converts it to a comma separated value document with values enclosed in quotes. Suited best for conversion of textual content. Probably will break with enough complexity within the table cells (ie much schema). Then again, this sort of data you probably don't need in CSV.

## vcard-out

Extract an entire record of a vcard (vcf) file based on a case-insensitive search pattern. See the script for details.

## Others

+ `audio_control`: an interface to music player functions (pause, forward, back, etc). I also incorporated controls for the Spotify Linux client. 
+ `countdown`: displays a countdown for the specified interval in seconds. A friendlier version of the basic *sleep* command.
+ `csv_to_markdown_table`: Convert the STDIN supplied comma-separated table (with headings) to the simple markdown table format. I assigned this to a VIM visual-mode mapping as such:

    ```vim
    autocmd Filetype markdown,rmd vnoremap ,t :!~/scripts/csv_to_markdown_table<cr>
    ```
+ `status-mon`: outputs some system information to the console. Outputs more with the -A flag.
+ rsync-wrap: A wrapper for *rsync* using common parameters.
