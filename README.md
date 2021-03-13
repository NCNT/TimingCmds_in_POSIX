# Timing Management Commands in POSIX

## What is this?

This is a command set to make your UNIX life more convenient! On the current POSIX commands, are you satisfied for timing management? Unfortunately, we aren't. That is because POSIX doesn't release the commands for controling time accurately and/or precisely. For instance, image a scene you have to send text data at one second interval accurately. How can you do that? You can probably do only like that.

```sh:
cat /PATH/TO/textdata_source |
while IFS= read -r line; do
  printf '%s\n' "$line"
  sleep 1
done
```

However, that is not accurate because extra time is required to execute `while` ~ `done` sentence and `printf`. So, we made some commands to solve such problems.

To solve the above problem, you can use `valve` command by the following.

```sh:
$ cat /PATH/TO/textdata_source | valve -l 1s
```

Several more commands are available.

* [`calclock`](bin/calclock) ... Convert bewteen the Calendar time and UNIX time
* [`getftimes`](c_src/getftimes.c) .. Display timestamps (mtime, ctime, atime) of a file
* [`linets`](c_src/linets.c) ..... Add timestamp to every line of text data
* [`ptw`](c_src/ptw.c) ........ A command wrapper to prevent a command from do full-buffering
* [`sleep`](c_src/sleep.c) ...... Sleep command which supports sleeping during less than a second
* [`tscat`](c_src/tscat.c) ...... Output each line at the data and time which is written in the top of the line
* [`valve`](c_src/valve.c) ...... Output each byte/line at the specified interval

To get the information for the commands, build the command and run them with the option `--help`.

## How to Build

First, `git clone` this repository. Then, run the `MAKE.sh` command to build the command with the source files.

To short, all you have to do is to type the following commands.

```sh:
$ git clone https://github.com/NCNT/TimingCmds_in_POSIX.git
$ c_src/MAKE.sh -d ../bin
```

And you can get the command in the `bin` directory. Copy or move them to one of directories which is listed in the `$PATH` variable.
Enjoy!

## Author / License

Tomoyuki Matsuura as Colonel Richie, belongs to USP-NCNT project and ShellShoccar Japan.

Everything in this repository is completely free for everyone. If you want any license to use them by all means, we'll give you [CC0](https://creativecommons.org/share-your-work/public-domain/cc0) or [the Unlicense](https://unlicense.org/). Anyway, take them freely as you like.
