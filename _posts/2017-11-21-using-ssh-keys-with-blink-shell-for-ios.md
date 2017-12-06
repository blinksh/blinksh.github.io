---
layout: post
title: "Using SSH Keys with Blink Shell for iOS"
description: "Using SSH Keys with Blink Shell for iOS"
keywords: "blink, ssh keys, blink shell, ios"
---

# Summary

This article will give an overview of what SSH keys are and describe how to use them in Blink.

# About SSH Keys

SSH (Secure Shell Keys) are small text files meant to be exchanged in lieu of passwords for verifying access to a remote server.  An SSH key comprises of two parts: a public key and a private key.  The public key is what resides on the remote server, and the private key is what resides on your local device.  The public key is not a secret, but the private key should never be shared with anyone nor uploaded to any untrusted location.

Using SSH keys is more secure than passwords as they are more difficult to crack compared to typical password.  For example, using standard computing power, it may take over a million years to crack an SSH key, but a standard password will take far less time to compromise.  Additionally, SSH keys are more convenient as you don’t have to type your password in each time you want to connect to a remote server.

# Using SSH Keys in Blink

Before you can use SSH keys you must generate or import a keypair.  In this article we will discuss generating a keypair.  To get started, run the config command in Blink to access the necessary configuration screen.

![]({{ site.baseurl }}/assets/images/posts/2017/using-ssh-keys-with-blink-shell-for-ios/image2.png)

Once you do this, the Settings dialog will open as shown below:

![]({{ site.baseurl }}/assets/images/posts/2017/using-ssh-keys-with-blink-shell-for-ios/image5.png)


Click on the Keys button to enter the SSH keys menu.

![]({{ site.baseurl }}/assets/images/posts/2017/using-ssh-keys-with-blink-shell-for-ios/image1.png)

In the above example we see that there is a default key named `id_rsa`.  The default key is always named `id_rsa` and this will be the key used first to authenticate.  You can have multiple SSH keys to connect to multiple SSH servers.  To create a key, click the + icon at the top and you will be presented with the New RSA Key dialog as shown below:

![]({{ site.baseurl }}/assets/images/posts/2017/using-ssh-keys-with-blink-shell-for-ios/image4.png)

Blink creates a default key named `id_rsa`.  If you wish to create another key, please give a descriptive name of your choosing.  As a suggestion, if you are going to generate a specific key pair for access to a specific server, we would recommend naming the key the hostname of that server.

A 2048 bit key is probably large enough, but you can choose a 4096 bit key for extra security if you desire.  

If you wish, you may provide a passphrase for your key.  This will encrypt the private key so that if it is ever compromised it will not be useable without knowing the passphrase.  An SSH connection is still encrypted and secure if you choose not to protect your key, but if you do, you will ensure an extra measure of security.  Keep in mind that the encryption of your private key is only as good as the passphrase you choose to use.  You can use a website like [How Secure is My Password](https://howsecureismypassword.net/) to determine the strength of your passphrase.

Blink stores your private key on the iOS Keychain, which is quite secure as it is protected through Secure Enclave.  So even if you choose not to protect your private key with a passphrase, it is still stored in a secure area on your device.

# Adding a Public Key to a Remote Host

The Blink command `ssh-copy-id` command can be used to copy the public key to a remote host.  This will effectively install the key for use in your connection to that server.  The syntax of the command is:

```
ssh-copy-id identity_file user@host
```

The identity_file argument is the name of your SSH key pair. The user is the remote username, and the host is the remote hostname.  You may also specify an IP address instead of a hostname if so desired.

![]({{ site.baseurl }}/assets/images/posts/2017/using-ssh-keys-with-blink-shell-for-ios/image3.png)

Establishing A Connection Using SSH Keys
There are two different ways to establish a connection to a remote server - via ssh or via mosh.  SSH will work in all cases, but if Mosh is available, it is preferred for mobile devices or internet / network connections that may encounter high latency or frequent disconnects.

To connect via SSH:

```
ssh user@1.2.3.4
```

In this example, an SSH connection is established with the username user to the remote IP 1.2.3.4.  You may also specify a hostname instead of an IP address.  Since no key was specified, the default key `id_rsa` will be used.

```
ssh -i your_key myhost
```

In the above example, the key `your_key` is used to connect to the pre-defined host myhost.  You can add pre-defined hosts in the Hosts section of the application, as discussed here (link to this document).

To connect with Mosh, the syntax is mostly the same:

```
mosh -I your_key host
```

In this example, your_key is the SSH key to use, and host is the host entry to use in the connection.
