waitforit(1) -- Wait until SSH becomes available.
=============================================

## SYNOPSIS

`waitforit <TARGET_HOST> [<TARGET_PORT> <MAX_RETRIES> <WAIT_SECONDS> <VERBOSE>]`

`waitforcpu <MIN_FREE_CPU_PERCENT> [<TIMEOUT> <WAIT_SECONDS> <VERBOSE>]`

## DESCRIPTION

waitforit will wait for an SSH port/service to become available and ready.
Blocking the shell until the SSH port is open.
Good for testing if an SSH host has rebooted and then continue running the
shell. Waits 3 seconds between each new connection attempt. If timeout occurs
the program will exit with a RC of 1.

waitforcpu will wait until the CPU usage is below the specified percentage. If
the CPU usage is already below the specified percentage, the program will
exit. The program will wait 3 seconds between each new check. If timeout occurs
the program will exit with a RC of 1.

## WAITFORIT OPTIONS

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

## WAITFORCPU OPTIONS

* `-h`, `--help` :
  Displays the help screen.

* `<MIN_FREE_CPU_PERCENT>` :
  The minimum free CPU percentage before the program exits. Integer value.

* `<TIMEOUT>` :
  The maximum time to wait, in seconds, before the program exits. Integer
  value. Default is 200 seconds.

* `<WAIT_SECONDS>` :
  Sleep/wait x seconds before starting to check, integer value. Default is 0.

* `-v, <VERBOSE>` :
  Be more verbose. Shows the result of the current CPU usage and the timeout
  left.

## EXAMPLES

Check if example.org has an open SSH port on port 7777. Abort after two failed
attempts.

    $ waitforit example.org 7777 2

Wait 20 seconds before checking if localhost has an open SSH port on port 22.
Abort after 10 failed attempts. Also show each connection attempt.

    $ waitforit localhost "" 10 20 -v

Block the shell until the CPU usage is below 90%. Abort after 200 seconds.

    $ waitforcpu 90

Block the shell until the CPU usage is below 5%. Abort after 20 seconds. Also
wait 10 seconds before starting to check. Also show the current CPU usage.

    $ waitforcpu 5 20 10 -v

## COPYRIGHT

See license file

## SEE ALSO

sleep(1), socat(1), top(1)
