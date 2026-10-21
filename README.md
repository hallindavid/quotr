# quotr

Prints one random quote, in green, when you open a terminal.

A single POSIX `sh` script. Works on macOS and Linux (including Alpine/BusyBox) with no extra installs.

## Install

Link the script into a folder that is already on your `PATH`, such as `~/.local/bin`:

```sh
ln -s "$PWD/quotr" ~/.local/bin/quotr
```

Then add this line at the **end** of `~/.zshrc` (macOS) or `~/.bashrc` (Linux):

```sh
command -v quotr >/dev/null && quotr "$HOME/quotes.md"
```

Keep the quotes around the path so spaces work.

## Choosing the quotes file

Pass the path as the first argument: `quotr /path/to/Quotes.md`. With no argument, `quotr` reads `~/.quotes.md`.

`quotr` only reads the file. If it is missing, unreadable, or has no quotes, `quotr` prints nothing and exits 0, so it never breaks shell startup.

## File format

A Markdown file. Each line that starts with `- ` (dash, space) is a quote. Every other line is ignored, so headings, notes and front matter are fine.

```markdown
# Quotes

Anything here is ignored.

- Travel far and wide, and you shall possess the secrets of men.  -The Hávamál
- Common sense is your best friend.  -The Hávamál
```

The leading `- ` and trailing whitespace are stripped. Indented bullets are ignored. See `quotes.md` for a full example.

## Color

Green only when output goes to a terminal and `NO_COLOR` is not set. `quotr | cat` prints plain text.
