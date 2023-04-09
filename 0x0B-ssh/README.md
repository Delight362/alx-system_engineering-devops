
#Generating an SSH Key Pair#

Generating a new SSH public and private key pair on your local computer is the first step towards authenticating with a remote server without a password. Unless there is a good reason not to, you should always authenticate using SSH keys.

A number of cryptographic algorithms can be used to generate SSH keys, including RSA, DSA, and ECDSA. RSA keys are generally preferred and are the default key type.

To generate an RSA key pair on your local computer, type:

    ssh-keygen

Generating public/private rsa key pair.
Enter file in which to save the key (/home/demo/.ssh/id_rsa):

This prompt allows you to choose the location to store your RSA private key. Press ENTER to leave this as the default, which will store them in the .ssh hidden directory in your user’s home directory. Leaving the default location selected will allow your SSH client to find the keys automatically.

Enter passphrase (empty for no passphrase):
Enter same passphrase again:

The next prompt allows you to enter a passphrase of an arbitrary length to secure your private key. By default, you will have to enter any passphrase you set here every time you use the private key, as an additional security measure. Feel free to press ENTER to leave this blank if you do not want a passphrase. Keep in mind though that this will allow anyone who gains control of your private key to login to your servers.

If you choose to enter a passphrase, nothing will be displayed as you type. This is a security precaution.

Output
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
The key fingerprint is:
8c:e9:7c:fa:bf:c4:e5:9c:c9:b8:60:1f:fe:1c:d3:8a root@here
The key's randomart image is:
+--[ RSA 2048]----+
|                 |
|                 |
|                 |
|       +         |
|      o S   .    |
|     o   . * +   |
|      o + = O .  |
|       + = = +   |
|      ....Eo+    |
+-----------------+

This procedure has generated an RSA SSH key pair, located in the .ssh hidden directory within your user’s home directory. These files are:

    ~/.ssh/id_rsa: The private key. DO NOT SHARE THIS FILE!
    ~/.ssh/id_rsa.pub: The associated public key. This can be shared freely without consequence.

Generate an SSH Key Pair with a Larger Number of Bits

SSH keys are 2048 bits by default. This is generally considered to be good enough for security, but you can specify a greater number of bits for a more hardened key.

To do this, include the -b argument with the number of bits you would like. Most servers support keys with a length of at least 4096 bits. Longer keys may not be accepted for DDOS protection purposes:

    ssh-keygen -b 4096

If you had previously created a different key, you will be asked if you wish to overwrite your previous key:

Overwrite (y/n)?

If you choose “yes”, your previous key will be overwritten and you will no longer be able to log in to servers using that key. Because of this, be sure to overwrite keys with caution.
Removing or Changing the Passphrase on a Private Key

If you have generated a passphrase for your private key and wish to change or remove it, you can do so easily.

Note: To change or remove the passphrase, you must know the original passphrase. If you have lost the passphrase to the key, there is no recourse and you will have to generate a new key pair.

To change or remove the passphrase, simply type:

    ssh-keygen -p

Enter file in which the key is (/root/.ssh/id_rsa):

You can type the location of the key you wish to modify or press ENTER to accept the default value:

Enter old passphrase:

Enter the old passphrase that you wish to change. You will then be prompted for a new passphrase:

Enter new passphrase (empty for no passphrase):
Enter same passphrase again:

Here, enter your new passphrase or press ENTER to remove the passphrase