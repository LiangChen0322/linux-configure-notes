ubuntu waiting for apt-get to exit

http://ccm.net/faq/810-unblocking-apt-get
If you ever encounter a failure with apt-get, perform the operations on a console under root:
Kill the process named apt-get: killall -9 apt-get
Reconfigure dpkg: dpkg --configure -a
Update apt-get: apt-get update
http://www.ubuntuupdates.org/ppa/google_chrome

