# making a C64 BASIC parser with node/gulp

Make it possible to code C64 BASIC in a text editor, using labels instead of line numbers,
and proper variable names. Convert the master file to a pure basic txt file and optionally
a prg file.

watch task that listens to file changes and triggers the conversion

set up as a bash script that can be started like this:  
```
$ z.basic [-w|-watch] [-h|-help] <filename>
```
optional argument -w (or -watch) to continue watching for changes after the initial build.
-h (or -help) to display useful things about the parser and the code structure

- auto line numbers
- labels (goto/gosub) translated to line numbers
- variables translated to AA AB AC AD
- support /* comments */ and // comments
- compile to prg
- toggle warp mode (config)
- toggle autostart x64 (config)


convert code.txt to .prg
$ petcat -w2 -o out.prg code.txt

start vice with prg file loaded
$ x64 out.prg

start vice with warp mode enabled
$ x64 -warp out.prg

## todos

- setup basic node/gulp project
- add task with command line params
- option to watch for changes
- convert: strip comments and empty lines and save to file
- convert: add line numbers and save to file
- load options (if any) on top of file
- take options into account
- detect labels for GOSUB/GOTO
- detect VARIABLES
- add verbose help option