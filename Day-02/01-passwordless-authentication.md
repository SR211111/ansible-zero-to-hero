# How to setup Passwordless Authentication

## EC2 Instances

### Using Public Key

```
ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>
```

- ssh-copy-id: This is the command used to copy your public key to a remote machine.
- -f: This flag forces the copying of keys, which can be useful if you have keys already set up and want to overwrite them.
- "-o IdentityFile <PATH TO PEM FILE>": This option specifies the identity file (private key) to use for the connection. The -o flag passes this option to the underlying ssh command.
- ubuntu@<INSTANCE-IP>: This is the username (ubuntu) and the IP address of the remote server you want to access.

### Using Password 

For target server/ Manage node
- Go to the file `/etc/ssh/sshd_config.d/60-cloudimg-settings.conf`
- Here you can not edit the file so you have to use sudo vi filename
- Update `PasswordAuthentication yes`
- Restart SSH -> `sudo systemctl restart ssh`
- set the password on the target server using command - sudo passwd ubuntu

- For ansible server/Contrl node
- ssh-copy-id ubuntu@51.20.87.131-public id
- type yes

