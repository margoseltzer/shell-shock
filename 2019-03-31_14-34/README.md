
# shellshock

Authors: Xueyuan Michael Han

Seed: 43670961620410975231081934347800654831

## Description


A simple ShellShock example to demonstrate:

* Xanthus' ability to reproduce different types of attacks

A standard Ubuntu 18.04 server is listening at port 8080.
A victim machine monitored by CamFlow is given a maliciously-formatted bash function definition with trailing code.
The code is executed and opens up a connection with the server.
The spawned bash session on the victim because of the bash vulnerability takes standard input from the server,
which is echoed by the server to be "uname -r ; ls".
The standard output and standard error are also sent to the server, so essentially,
a reverse TCP shell is created where any command provided by the server will be executed on the victim,
and the results of the command will be sent to the server.
Secret information of the victim machine is therefore exfiltrated.
The attacker also create a new file `.bad_configrc` in the victim machine.
The file can be a cronjob that further creates damage.

In this example, we redirect the output of the commands to a temporary file called "secrets.txt"
to demonstrate that information was indeed exfiltrated.

Everything is done automatically through scripts for reproducility with minimum human interaction.

      