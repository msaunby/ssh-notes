# ssh-notes
Tips on using ssh

Author: Michael Saunby
Date: 31 October 2024
Rev: 0.1

## Purpose

Tips for common uses of ssh.

## Raspberry Pi

<https://www.raspberrypi.com/documentation/computers/remote-access.html#ssh>

## Ubuntu

<https://ubuntu.com/server/docs/openssh-server>

## GitHub

<https://docs.github.com/en/authentication/connecting-to-github-with-ssh>

## Ssh tools

<https://www.openssh.com/>

### ssh-keygen

Although the default key type for ssh was RSA for a very long time, this is now deprecated (obsolete).  It is possible to continue using ssh-rsa but for new keys it is better to use a newer, more secure, algorithm, e.g. ed25519

```sh
% ssh-keygen -t ed25519
```

When deciding whether to set a pass-phrase consider how you will be using the key.  If you are using ssh-agent it probably won't be a burden, but for some uses it's far easier to just specify a key to use and have everything run without prompts for the pass-phrase - this is how I work with VC Code remotes.

### ssh-agent

Once you have a key pair you will need to copy the public key to the remote system you wish to log in to.

One way of diong this is as follows.

```sh
% eval "$(ssh-agent -s)"
% ssh-add id_ed25519
% ssh-copy-id username@remote.host.com
```
