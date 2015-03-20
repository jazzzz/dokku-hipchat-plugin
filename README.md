# dokku-hipchat-plugin

## Installation
````
	git clone https://github.com/gcohen55/dokku-hipchat-plugin.git /var/lib/dokku/plugins/hipchat
	dokku plugins-install
````

Quick How-To:
Get your HipChat API V2 Token, Room ID, and come up with a From Name that you'd like to see in HipChat from Dokku for any hooks/notifications/etc involving your application.
````
	dokku hipchat:settings <app> <hc v2token> <hc room id> <hc from>
	dokku hipchat:enable <app>
	dokku hipchat:test
	# now verify that test message showed up in hipchat. if it did, you should receive notifications from dokku on future deployments/builds/etc
````

Example
````
	dokku hipchat:settings orderform 9300cabcdefabcd1913f1a0b1de5fc 41255 AwesomeApp
	dokku hipchat:enable <app>
	dokku hipchat:test
````

Possibilities are endless. Want to send custom messages from within a shell script as part of some other insane thing you want to do?
````
	echo "Completed doing database dump pre-upgrade"
	dokku hipchat:send_message orderform 'Completed doing database dump pre-upgrade for backup purposes.'
````


Reference:
````
    hipchat:settings <app> <hc v2token> <hc room id> <hc from>            Sets HipChat token, room id, from for app. /WILL/ overwrite old configuration. Does /NOT/ enable notifications.
    hipchat:info <app>                                                    General HipChat information for app
    hipchat:enable <app>                                                  Enables HipChat for app. Requires settings be defined using hipchat:settings
    hipchat:disable <app>                                                 Disables HipChat for app. Leaves configuration behind.
    hipchat:remove <app>                                                  Disables HipChat notifaction (this removes old config)
    hipchat:test <app>                                                    Sends a test message using previous settings
    hipchat:send_message <app> <message>                                  Sends message exactly as message, with no extra info or formatting.
````

## License

The MIT License (MIT)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[hipchat-cli]: http://github.com/hipchat/hipchat-cli