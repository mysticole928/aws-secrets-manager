# AWS Secrets Manager Snippets

I'm going to move this to another repo.  (Eventually.)

Initally, I thought I'd have a bunch of notes about every service.

The file `storing-ssh-pem-files.md` outlines how to store `pem` files in 
Secrets Manager.

Uploading to Secrets Manager using the console (depending on the browser) can
add newlines that break the `pem` files.

I'm working on a shell script to automate the uploading and downloading.  
