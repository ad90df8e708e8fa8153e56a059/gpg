# Common GPG Commands

##Print the available system entropy level
    cat /proc/sys/kernel/random/entropy_avail

##Generate a new public/private keypair
    gpg --gen-key

##Generate a revocation certificate
    gpg --gen-revoke "name"

##Print a public key to stdout
    gpg -a --export "name"

##Print a public key to a file
    gpg -a --export "name" > public.key

##Print a private key to file
    gpg -a --export-secret-key "name" > private.key

##Import a public or private key file to keyring
    gpg --import keyfile.gpg

##Remove a public key from keyring
    gpg --delete-key "name"

##Remove a private key from keyring
    gpg --delete-secret-key "name"

##Encrypt a file
    gpg -a -e -u "Sender" -r "Receiver" clear.txt > encrypted.gpg

##Decrypt a file
    gpg -d encrypted.gpg > clear.txt

##Verify a signature for "file.iso"
    gpg --verify file.iso.asc

##List public keys and their fingerprints
    gpg --list-public-keys --fingerprint

##List private keys and their fingerprints
    gpg --list-secret-keys --fingerprint

##Send a public key to a keyserver
    gpg --keyserver hkp://pgp.mit.edu --send-keys fingerprint

##Get a public key from a keyserver
    gpg --keyserver hkp://pgp.mit.edu --recv-keys fingerprint
    
##Search a keyserver for "name"
    gpg --keyserver hkp://pgp.mit.edu --search-keys "name"
    
##Change trust level for key in keyring
    gpg --edit fingerprint trust
