# Common GPG Commands

##Install gpg (Debian/Ubuntu)
    apt-get update
    apt-get install gpg -y

##Print the available entropy (Debian/Ubuntu)
    cat /proc/sys/kernel/random/entropy_avail

##Install rng-tools (Debian/Ubuntu)
    apt-get install rng-tools -y
    echo "HRNGDEVICE=/dev/null" >> /etc/default/rng-tools
    echo "RNGDOPTIONS="-r /dev/urandom" >> /etc/default/rng-tools
    service rng-tools restart

##Generate a new public/private keypair
    gpg --gen-key

##Generate a revocation certificate
    gpg --gen-revoke "name"

##Print a public key to stdout
    gpg -a --export "name"

##Print a public key to a file
    gpg -a --export "name" -o public.key

##Print a private key to file
    gpg -a --export-secret-key "name" -o private.key

##Import a public or private key file to keyring
    gpg --import keyfile.gpg

##Remove a public key from keyring
    gpg --delete-key "name"

##Remove a private key from keyring
    gpg --delete-secret-key "name"

##Encrypt a file
    gpg -a -e -u "Sender" -r "Receiver" clear.txt -o encrypted.gpg

##Decrypt a file
    gpg -d encrypted.gpg -o clear.txt

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
