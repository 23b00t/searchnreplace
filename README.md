# snr: Search and Replace Script

This script allows for searching and replacing text within files using regular expressions. It supports both case-sensitive and case-insensitive searches and can read from standard input or from files in a specified directory.
It is meant for project-wide search and replace operations with the advantage of a preview of the replacements in question.

## Prerequisites ##
- Ensure you have `ripgrep` installed on your system. You can find it at [ripgrep GitHub Repository](https://github.com/BurntSushi/ripgrep).

## Usage ##
``` bash
snr [Options] search_expression replace_expression [path]
```

## Options ##
- `-i`: Perform a case-insensitive search.
- `-p`: Specify a path for a recursive search. The path must be the last argument.
- `-h`: Display help information about usage.

## Behavior ##
- When the `-p` option is provided, the script will recursively search the specified directory for files containing the search term.
- If no path is provided (i.e., `-p` is not used), the script will read input from standard input (stdin). For example:
``` bash
rg -l --max-depth 1 "search_term" | snr search_term replace_with
```
- Search and replace operations utilize regex, and spaces or special characters should be enclosed in quotes.

## Examples ##
1. Replace "old" with "new" in files under the current directory:
``` bash
snr old new
```

2. Perform a case-insensitive replacement of "hello" with "hi" in files under the `documents` directory:
``` bash
snr -ip hello hi documents
```

3. Display help information:
``` bash
snr -h
```

## Note ##
- The script prompts for confirmation before making replacements in each file.
- All replacements will be made in-place, meaning the original files will be modified.

## License ##
This script is released under the MIT License.
