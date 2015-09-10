#!/bin/bash

# define default values
CMDFILE="save"

# help information
HELPSTRING="mac_update.sh v0.1 bash script to update command line applications
    -a or --add-cmd + VALUE adds a command to the command file
    -f or --cmdfile + VALUE runs a certain file (must have .cmd extension), by default the file is save.cmd
    -c or --clear   + VALUE deletes a file with commands (must have .cmd extension)
    -q or --quiet           suppress output
    -h or --help            displays help information"

# parse arguments
# from http://stackoverflow.com/questions/192249
while [[ $# > 0 ]]
do
key="$1"

case $key in
    -a|--add-cmd)
    ADDCMD="$2"
    shift
    ;;
    -f|--cmdfile)
    CMDFILE="{$2%.cmd}"
    shift
    ;;
    -c|--clear)
    CLEAR="$2"
    shift
    ;;
    -q|--quiet)
    QUIET=" 2&>1 >/dev/null"
    ;;
    -h|--help)
    echo "$HELPSTRING"
    exit
    ;;
    *)
    echo "$HELPSTRING"
    exit    # unknown option
    ;;
esac
shift # past argument or value
done

# generate .cmd file if needed
if [ "$CMDFILE" != "" ];
then
    CMDFILE="$CMDFILE.cmd"
fi

# add command to file
if [ "$ADDCMD" != "" ];
then
    cat "$ADDCMD" >> "$CMDFILE"
    exit
fi

# remove file
if [ "$CLEAR" != "" ] && [ -f "$CLEAR" ];
then
    rm "$CLEAR"
fi

# loop over lines in file
while IFS='' read -r line || [[ -n $line ]]; do
    rmcomment="${line%#*}$QUIET" # remove comments and suppress output if needed
    $rmcomment                   # run command
done < "$CMDFILE"

echo "All up-to-date."
