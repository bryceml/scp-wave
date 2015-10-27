scpWave is a Python script used for transferring files to Unix machines on a cluster. The script uses the scp utility to carry out the transfers starting with a single seed. As more files are transferred, the number of seeders increases and we see a logarithmic speed up versus a sequential transfer.

A more efficient file transfer script can be found here:
https://code.google.com/p/scp-tsunami/