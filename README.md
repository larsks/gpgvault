Scripts for encrypting your Ansible vault password with GPG.

Inspired by "[Using PGP To Encrypt The Ansible Vault][call]", by Erin
Call.

[call]: https://blog.erincall.com/p/using-pgp-to-encrypt-the-ansible-vault

## Example

Initialize your project:

    $ git init myproject
    $ cd myproject
    $ gpgvault init -g 
    generated 512 bit key in .vault-password.gpg
    Initialized gpgvault in /Users/lars/tmp/myproject
    $ ls -A
    .git      .vault-password.gpg
    .gitattributes    ansible.cfg

Create a vault file (which should end in `.vault` if you want `git
diff` to work, otherwise it doesn't matter):

    $ ansible-vault create secrets.vault

If you haven't recently used your GPG passphrase, you should now be
prompted to enter it, assuming your agent is set up correctly.  You
can then try:

    $ ansible-vault view secrets.vault

And that should Just Work, without requiring any additional password
input on your part (until the cached key in your agent expires, after
which you will need to re-authenticate).
