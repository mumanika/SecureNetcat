# SecureNetcat
A secure file transfer service that encrypts with AES-GCM. Allows for bidirectional file transfer and integrity verification.

The secure netcat script is an approximation of netcat that implements a secure file transfer from a client to a server or vice-versa. The encryption technique that is used is AES-GCM. 
The script verifies the integrity of each chunk of message that is sent across the network and received at either the server or the client. 

Pre-requisites: 
###############
This program was developed and tested on a Unix environment that hosted Python 3.7.5. Please use a Linux or Unix machine with this version in order to get started. 

Installation:
#############
The program makes use of Python's argument parser library and pycryptodome in order to carry out it's functions.
Please check the requirements.txt file and install these packages using the command: "pip3 install <package_name>".
In addition to this, the socket, sys, select and base64 modules are utilised.

Place the script in the desired directory and ensure that the file has executable permissions. You can achieve this by using the following command: "chmod +x snc".

Running the program: 
####################
Once you are in the directory where the scriptfile is present, you will have to run the following command if you plan to run the program as a server: 
[server]$ ./snc --key CSC574ISAWESOME -l 9999 > some-file.txt

On the client side, you may run the script as follows: 
[client]$ ./snc --key CSC574ISAWESOME server.add.ress 9999 < some-file.txt

The script will copy the contents of some-file.txt specified as input to the client and transfer that in a secure manner to the server's standard output. In this case it will create a file in the server called some-file.txt. 

The users are free to specify files to transfer in any direction as the program supports bidirectional transfer capability. As such, the command line is conformant to: 

[client]$ ./snc --key CSC574ISAWESOME server.add.ress 9999 < file1-in.txt > file2-out.txt
[server]$ ./snc --key CSC574ISAWESOME -l 9999 > file1-out.txt < file2-in.txt

The parameters of the commands are: 
--key : This is the password that the user must provide in order to securely encrypt the data that is being transferred. This is a mandatory parameter.
-l: This specifies that the program will run in server mode. 
Ensure that a valid port number and address if provided (if in client mode) or the script will not start. 
> : Specifies output redirection
< : Specifies input file

Author: 
#######
Mukul Manikandan(mmanika@ncsu.edu)
