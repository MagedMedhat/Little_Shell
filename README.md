# LSH — Libstephen Shell (Modified Fork)

> This project is based on [Stephen Brennan's LSH](http://brennan.io/2015/01/16/write-a-shell-in-c/) — a simple shell implementation in C written as a tutorial to demonstrate the basics of how a shell works.
> I cloned the original code, studied it, and extended it by implementing four new built-in commands from scratch.

---

## What's New

The following built-in commands were added to the original project:

| Command   | Description                                      |
|-----------|--------------------------------------------------|
| `pwd`     | Print the current working directory              |
| `echo`    | Print arguments to the terminal                  |
| `env`     | Print all environment variables                  |
| `history` | Print the list of previously entered commands    |

### History Implementation Details

The history feature uses **dynamic memory allocation** — it grows automatically as you enter more commands, with no fixed limit:

- Starts with capacity for 10 entries
- Expands by 10 each time it fills up
- Each entry is a copy of the command string (`strdup`)
- All memory is freed cleanly when you type `exit`

---

## Built-in Commands

| Command      | Description                                      |
|--------------|--------------------------------------------------|
| `cd <dir>`   | Change the current directory                     |
| `pwd`        | Print the current working directory              |
| `echo <...>` | Print arguments to stdout                        |
| `env`        | Print all environment variables                  |
| `history`    | Print command history                            |
| `help`       | List all built-in commands                       |
| `exit`       | Exit the shell                                   |

---

## Running

Compile with:

```bash
gcc -o lsh main.c
```

Then run:

```bash
./lsh
```

To use the standard-library based `lsh_read_line()` instead:

```bash
gcc -DLSH_USE_STD_GETLINE -o lsh main.c
```

---

## Known Limitations

These are inherited from the original project and have not been changed:

- Commands must be on a single line
- Arguments must be separated by whitespace
- No quoting arguments or escaping whitespace
- No piping or redirection

---

## Original Project

This project is based on the tutorial **"Write a Shell in C"** by Stephen Brennan.

- Tutorial: http://brennan.io/2015/01/16/write-a-shell-in-c/
- Original author: Stephen Brennan

---

## License

This code is in the public domain — see [UNLICENSE](UNLICENSE) for details.
You can use, modify, and distribute it freely without any restriction.