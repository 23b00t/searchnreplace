# snr: Search and Replace Script

This script allows for searching and replacing text within files using regular expressions. It supports both case-sensitive and case-insensitive searches and can read from standard input or from files in a specified directory. The default directory is `./`
It is meant for project-wide search and replace operations with the advantage of a preview of the replacements in question.

## Prerequisites ##
- Ensure you have `ripgrep` installed on your system. You can find it at [ripgrep GitHub Repository](https://github.com/BurntSushi/ripgrep).

## Usage ##
``` bash
snr [Options] search_expression replace_expression [path]
```

## Options ##
- `-i`: Perform a case-insensitive search.
- `-r`: Reads filenames from stdin (instead of searching ./path)
- `-o`: For rg options, e.g. snr -po -. search_term replace_with (to search hidden files too)
- `-h`: Display help information about usage.

## Examples ##
1. Replace "old" with "new" in matching files under the current directory:
``` bash
snr old new
```

2. Perform a case-insensitive replacement of "hello" with "hi" in files under the `Documents` directory:
``` bash
snr -i hello hi ~/Documents
```

3. Pass Options to rg to search in hidden files:
``` bash
snr -o -. hello hi ./
```

4. Use extended RegExp to search case case-insensitive all files in the current path for `username: ` followed by any name and replace it with `username: Daniel`:
``` bash
snr -io -. '(username: ).*' '\1Daniel'
```

5. Read filenames to search and replace from StdIn ():
``` bash
find ./ -type f -size +1M | snr -r search_term replace_with
```

6. Display help information:
``` bash
snr -h
```

## Note ##
- The script prompts for confirmation before making replacements in each file.
- All replacements will be made in-place, meaning the original files will be modified.

## License ##
This script is released under the MIT License.
