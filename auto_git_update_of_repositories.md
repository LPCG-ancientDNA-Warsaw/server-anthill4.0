How does the automatic push and pull for the scripts and conf directories work?
================
LAST EDIT: 30th September 2026

# Automatic push of edits done on server anthill4.0 to the directories scripts/ and conf/

I recently activated an automatic system that pushes edits done on anthill 4.0 server on the repositories scripts/ and conf/. 
This only works from the server to the GitHub repository, and not the contrary: this feature is intended to work like this, to
ensure that accidental edits done on GitHub do not get accidentally merged on the server.

### How to work on the server

0. Before editing any scripts, it is advisable to check if there are any edits done on GitHub Web to synchronize, using `command git rev-list --count HEAD..origin/main`. The output of this command is the number of commits that are currently not resolved.
1. Please work normally on the server, editing the scripts as you deem fit.
2. You don't need to remember to push or pull your code (if you do, though, that is better).
3. Every night, at 23:00, an automatic process will update the GitHub repository.

This is what happens behind the scenes:
Edit on server --> 23:00 automatic system activates --> Is there an unresolved edit on Github that was not pushed to the server? --> NO --> Great! Push the code on the server to the Github Repository --> Removes (if existent) REMOTE_CHANGES_WARNING.log
                                                                                                                            └────--> YES -> Bad --> Does not push the code --> Creates a REMOTE_CHANGES_WARNING.log file to notify the problem

### What do do if you find the file REMOTE_CHANGES_WARNING.log
If you find this file on the server, that means that someone has edited the files directly on GitHub Web and synchronization is temporarily suspended.
In this case, to avoid conflicts, execute from terminal:

```git pull origin main```

If the file that was edited is the one you are working on, git will ask you to either keep or discard the edits. Check the two versions of the documents to keep or discard edits. 
After pulling the code and resolving the conflicts, the .log file will disappear and daily syncrhonization will resume normally.
