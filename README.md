# yubikeylockd

Simple daemon for locking and unlocking OS X with Yubikey.


## Install

Run make and make install


## Additional requirements
  * Configured integration with Yubico PAM module
  * Require password *immediately* after sleep or screen saver begins
  ![](http://i.imgur.com/URXUukP.png)

## How it works

When you attach Yubikey for the first time launchctl will run yubikeylockd daemon
that will simply monitor the state of the given USB device.
Daemon based on the sample provided by Apple for IOKit development.

It does two things: 
* when device is attached it makes activity via
```IOPMAssertionDeclareUserActivity``` call to turn screen on
* after device is detached it runs shell command ```pmset displaysleepnow```
 to put display to sleep and (if you configured it) also lock the OS X
