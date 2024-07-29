Step 1 :
sudo su
#apt install -y asterisk

Step 2 :
#mv /etc/asterisk/sip.conf /etc/asterisk/sip.conf.orig
#nano /etc/asterisk/sip.conf

[general]
context=internal
allowguest=no
allowoverlap=no
bindport=5060
bindaddr=0.0.0.0
srvlookup=no
disallow=all
allow=ulaw
alwaysauthreject=yes
canreinvite=no
nat=yes
session-timers=refuse
localnet=192.168.3.1/255.255.255.0

[7001]
username=7001
type=friend
host=dynamic
secret=123
context=internal

[7002]
username=7002
type=friend
host=dynamic
secret=456
context=internal

[7003]
username=7003
type=friend
host=dynamic
secret=789
context=internal

[7004]
username=7004
type=friend
host=dynamic
secret=987
context=internal

[7005]
username=7005
type=friend
host=dynamic
secret=654
context=internal

[7006]
username=7006
type=friend
host=dynamic
secret=768
context=internal

[7007]
username=7007
type=friend
host=dynamic
secret=535
context=internal

[7008]
username=7008
type=friend
host=dynamic
secret=863
context=internal

Step 3 :
#mv /etc/asterisk/extensions.conf /etc/asterisk/extensions.conf.orig
#nano /etc/asterisk/extensions.conf

[internal]
exten => 7001,1,Answer()
exten => 7001,2,Dial(SIP/7001,60)
exten => 7001,3,Playback(vm-nobodyavail)
exten => 7001,4,VoiceMail(7001@main)
exten => 7001,5,Hangup()

exten => 7002,1,Answer()
exten => 7002,2,Dial(SIP/7002,60)
exten => 7002,3,Playback(vm-nobodyavail)
exten => 7002,4,VoiceMail(7002@main)
exten => 7002,5,Hangup()

exten => 7003,1,Answer()
exten => 7003,2,Dial(SIP/7003,60)
exten => 7003,3,Playback(vm-nobodyavail)
exten => 7003,4,VoiceMail(7003@main)
exten => 7003,5,Hangup()

exten => 7004,1,Answer()
exten => 7004,2,Dial(SIP/7004,60)
exten => 7004,3,Playback(vm-nobodyavail)
exten => 7004,4,VoiceMail(7004@main)
exten => 7004,5,Hangup()

exten => 7005,1,Answer()
exten => 7005,2,Dial(SIP/7005,60)
exten => 7005,3,Playback(vm-nobodyavail)
exten => 7005,4,VoiceMail(7005@main)
exten => 7005,5,Hangup()

exten => 7006,1,Answer()
exten => 7006,2,Dial(SIP/7006,60)
exten => 7006,3,Playback(vm-nobodyavail)
exten => 7006,4,VoiceMail(7006@main)
exten => 7006,5,Hangup()

exten => 7007,1,Answer()
exten => 7007,2,Dial(SIP/7007,60)
exten => 7007,3,Playback(vm-nobodyavail)
exten => 7007,4,VoiceMail(7007@main)
exten => 7007,5,Hangup()

exten => 7008,1,Answer()
exten => 7008,2,Dial(SIP/7008,60)
exten => 7008,3,Playback(vm-nobodyavail)
exten => 7008,4,VoiceMail(7008@main)
exten => 7008,5,Hangup()

exten => 8001,1,VoicemailMain(7001@main)
exten => 8001,2,Hangup()

exten => 8002,1,VoicemailMain(7002@main)
exten => 8002,2,Hangup()

exten => 8003,1,VoicemailMain(7003@main)
exten => 8003,2,Hangup()

exten => 8004,1,VoicemailMain(7004@main)
exten => 8004,2,Hangup()

exten => 8005,1,VoicemailMain(7005@main)
exten => 8005,2,Hangup()

exten => 8006,1,VoicemailMain(7006@main)
exten => 8006,2,Hangup()

exten => 8007,1,VoicemailMain(7007@main)
exten => 8007,2,Hangup()

exten => 8008,1,VoicemailMain(7008@main)
exten => 8008,2,Hangup()

Step 4 :
#mv /etc/asterisk/voicemail.conf /etc/asterisk/voicemail.conf.orig
#nano /etc/asterisk/voicemail.conf

[main]
7001 => 123

7002 => 456

7003 => 789

7004 => 987

7005 => 654

7006 => 768

7007 => 535

7008 => 863

Step 5 :
#service asterisk restart
or
#/etc/init.d/asterisk restart

Step 6 :
#asterisk -r
sip show peers
