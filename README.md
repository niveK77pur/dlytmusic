# dlytmusic
A program written around `youtube-dl` to make it easier to download music and keep track of your downloads.

Additionally to downloading music, this program also keeps track of your downloads through a log file. This is useful if you delete music or just want to easily find it back. This way the program can also verify whether you already have downloaded and installed a song which prevents you from downloading something twice.

# Usage
After installing the program, you can easily download music from youtube through this command:  
`dlytmusic.sh <URL>`

To get a quick help about the different commands use:  
`dlytmusic.sh -h` and  
`dlytmusic.sh -lh` to get help about the different listing options.

In order to play all the music you downloaded with this program use:  
`dlytmusic.sh -a`  
which will launch `nvlc` and play the music in random order.

Search for music by specifing the name or only part of the name:  
`dlytmusic.sh -s <PATTERN>`  
With the `-p` parameter you can play the music that matches the given pattern:  
`dlytmusic.sh -p <PATTERN>`  
which will launch `cvlc`. Don't panic if nothing pops up, because `cvlc` doesn't have an interface. If you like to exit, simply press `CTRL-C`.

# Put it inside your search path
Typically you create a `~/bin/` directory inside your home directory. This is where you store all you scripts because you might not want to touch `/bin/` or `/usr/bin/`. The `~/bin/` directory might already be part of your shell's search path, if not you should be able to append it (in bash) with the following command:  
`PATH=$PATH:~/bin`  
Put this line into your `.bashrc` to make it a permanent change. If you want to undo the change, simply remove the line from your `.bashrc` file.

Alternatively you could also create an `alias` to the `dlytmusic.sh` executable as follows:  
`alias blabla=~/Downloads/dlytmusic.sh`  
I used `blabla` to indicate that you can name your alias whatever you want. You can also call it `dlytmusic` if the extension bothers you. I like to keep the extension though, because that way I know which scripts I wrote and which have been downloaded.  
I assumed that you downloaded this program into your `Downloads` folder, but that doesn't have to be the case. Simply insert the path to your executable and done!

# Things you should note
When using this program for the first time a new directory is created: `~/Music/Youtube_Music/`  
This is where the program operated by default (i.e. downloading music, playing music with `-a`, searching music with `-s`, etc.). You can change the default directory by changing the `msc` variable at the top of the source code.

When downloading a music, the name alongside its url is saved to `downloadlist.csv` which is stored inside the default directory (specified by the `msc` variable). Don't alter its location because this way it is all grouped nice and tidy.

# Requirements
This program obviously uses `youtube-dl` so you have to download that first of all. You might also have to update it from time to time with the following command:  
`sudo youtube-dl --update`

In order to easily play music with this program, it also uses `cvlc` and `nvlc`. You will probably have to install `vlc` in order to access these.

Lastly the filebrowser that is used is `nautilus`. If you don't have that, you can either:  
  - Try to install `nautilus`
  - change the `browser` variable in the top of the program to contain the command for your filebrowser  
  
For the latter option you might also have to tweak the two lines of code which make use of the `$browser` command because the syntax might be a little different.
