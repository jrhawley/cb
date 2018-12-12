
# cb
## A leak-proof tee to the clipboard

This script is modeled after `tee` (see [`man tee`][2]).

It's like your normal copy and paste commands, but unified and able to sense when you want it to be chainable

## Examples


### Copy

```bash
$ echo -n $(date) | cb
# clipboard contains: Tue Jan 24 23:00:00 EST 2017
# but, because of `echo -n` there is no newline at the end
```

### Paste

```bash
# clipboard retained from the previous block
$ cb
Tue Jan 24 23:00:00 EST 2017
# above there is a newline after the output for readability
# below there is no newline because cb recognized that it was outputing to a pipe and any alterations would "contaminate" the data
$ cb | cat
Tue Jan 24 23:00:00 EST 2017$ cb > foo
# look carefully at this   ^^ that's a new $ prompt at the end of the content exactly as copied
$ cat foo
Tue Jan 24 23:00:00 EST 2017
```

### Chaining

```bash
$ date | cb | tee updates.log
Tue Jan 24 23:11:11 EST 2017
$ cat updates.log
Tue Jan 24 23:11:11 EST 2017
# clipboard contains: Tue Jan 24 23:11:11 EST 2017
```

  [1]: https://gist.github.com/RichardBronosky/56d8f614fab2bacdd8b048fb58d0c0c7
  [2]: 
http://man7.org/linux/man-pages/man1/tee.1.html