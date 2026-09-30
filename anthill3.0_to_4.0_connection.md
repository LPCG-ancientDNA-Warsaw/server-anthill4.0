Move files across servers.
================
LAST EDIT: 30th September 2026

# Tutorial on how to transfers files to and from the new server \[anthill\]\[ver0.4\]

### Requisites: have an account on the new server \[anthill\]\[ver0.4\]

You should have received an e-mail on your institutional e-mail, after
you supervisor has requested an account for you. In this e-mail you will
find the following information: 
login: your_account_name 
pass: one_time_link_for_your_password 
gid: group_name.

Log-in in the new server by running the following command and
substituting ‘login’ with your user name:

    ssh login@sih-17.cent.uw.edu.pl

There proceed to change your password with command `passwd`.

## 1. Transfer your files from the old server

If everything worked fine, you can test the pipeline on your own data.
To transfer your data from your folder in the old server (IP:
pier23.cent1.uw.edu.pl), log on IP pier23.cent1.uw.edu.pl and run this
command:

    scp -r ./<source_anthill3.0_folder> <your_username_in_new_anthill_server>@sih-17.cent.uw.edu.pl:<target_directory_anthill4.0_fullpath>

The `-r` flag is necessary to transfer directories and their files:
remove it if you wish to simply transfer files.

## 2. Transferring your files back to the old server
If you need to transfer files back to pier23 (regardless of whether you connect through the internal or external network), run this command:

    scp -r ./<source_anthill4.0_folder> <your_username_in_old_anthill_server>@so.cent.uw.edu.pl:<target_directory_anthill3.0_fullpath>

Mind that the "scp" command copies, not moves, the files so after use you have duplicated files one of which should be deleted, unless necessary.
