waitforit(1) -- Wait until SSH becomes available.
=============================================

## SYNOPSIS

`waitforit`
<TARGET_HOST> [<TARGET_PORT> <MAX_RETRIES> <WAIT_SECONDS> <VERBOSE>]

## DESCRIPTION

Wait for an SSH port/service to become available and ready. Good for testing if
an SSH host has rebooted and then continue running the shell. Waits 3 seconds
between each new connection attempt.

## OPTIONS

* `-h`, `--help` :
  Displays the help screen.

* `<TARGET_PORT>` :
  SSH portnumber

* `<MAX_RETRIES>` :
  The maximum attempts to try before program aborts and exist with 1. Default
  max connection retries is 200 (equals to around 10 minutes in total). Integer
  value.

* `<WAIT_SECONDS>` :
  Sleep/wait x seconds before starting to scan, integer value. Default is 0.

* `-v, <VERBOSE>` :
  Be more verbose. Shows the result of each connection attempt.

## EXAMPLES

Check if example.org has an open SSH port on port 7777. Abort after two failed
attempts.

    $ waitforit example.org 7777 2

Wait 20 seconds before checking if localhost has an open SSH port on port 22.
Abort after 10 failed attempts. Also show each connection attempt.

    $ waitforit localhost "" 10 20 -v

## COPYRIGHT

See license file

## SEE ALSO

sleep(1), socat(1)
