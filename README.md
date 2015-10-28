# scp-wave
Automatically exported from code.google.com/p/scp-wave

scpWave.py - binary tree distribution of files to hosts on a cluster using
             scp utility.

# SUMMARY
  Transfer a file to multiple hosts via scp utility

  The script begins by using the current machine to transfer a file to a host.
  Once this transfer is done, both the current machine and the host which
  received the file are used to send the same file to the next target hosts in
  the target queue. This continues to spread, adding more seeders until all
  targets have received the file (and thus become seeders themselves).


# USAGE
 ./scpWave.py <file> <file destination>

   Required Options - must specify a target host
     -l '<host1> <host2> <host3> ...'  # list the target hosts, quote multiples
     and/or
     -f <host file>                    # specify '\n' separated host file
     and/or
     -r '<basehost[a-b,c-d,...]>'      # eg. host[1-2,4-4] -> host1, host2, host4

    So, you can list hosts on the command line with -l or put them in a file
    separated by '\n' characters. You can also specify a range of hosts with -r.
    All three options: -l, -r, and -f may be used together. It is important to
    note that for the -l option, multiple hosts must be quoted.

    Other options
     -s Writes transfer statistics to a log file
     -u Specify a username to use for the transfers
     -v Enable verbose output

# LOGGING
  After each run, the results are written to "transfers.log" as comma separated
   values. This is the format:
   time, active seeds, transfers
   where time is the elapsed time to transfer "transfers" files.
   Use -s switch to turn on logging

 COMMAND - the command this script will use to transfer files
  For better performance, try '-c blowfish'
  Fill CMD_TEMPLATE with the seeder and target host data from seedq and targetq.
    CMD_TEMPLATE = "ssh -o StrictHostKeyChecking=no user@host1 scp -o\
    StrictHostKeyChecking=no/file user@host2:/file"

    CMD_TEMPLATE = "ssh -o StrictHostKeyChecking=no seeder[0] scp -o\
    StrictHostKeyChecking=no seeder[1] target[0]:target[1]"

# ISSUES
  1. ctrl-c behavior. 
     A thread will continue to try transferring after ctrl-c
     setting max_transfer_attempts to 1 seems to work

# TODO
  1. try 'ssh <host> exit' if transfer fails to see if host is up   
  2. 'received by: n hosts' doesn't print right at end

===============
The MIT License
Copyright (c) 2010 Clemson University
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
