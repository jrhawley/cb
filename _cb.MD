# cb
## A leak-proof tee to the clipboard

This script is modeled after `tee` (see [`man tee`][2]).

It's like your normal copy and paste commands, but unified and able to sense when you want it to be chainable

## Examples


### Copy

    $ date | cb
    # clipboard contains: Tue Jan 24 23:00:00 EST 2017
    
### Paste

    # clipboard retained from the previous block
    $ cb
    Tue Jan 24 23:00:00 EST 2017
    $ cb | cat
    Tue Jan 24 23:00:00 EST 2017
    $ cb > foo
    $ cat foo
    Tue Jan 24 23:00:00 EST 2017

### Chaining

    $ date | cb | tee updates.log
    Tue Jan 24 23:11:11 EST 2017
    $ cat updates.log
    Tue Jan 24 23:11:11 EST 2017
    # clipboard contains: Tue Jan 24 23:11:11 EST 2017


  [1]: https://gist.github.com/RichardBronosky/56d8f614fab2bacdd8b048fb58d0c0c7
  [2]: 
http://man7.org/linux/man-pages/man1/tee.1.html