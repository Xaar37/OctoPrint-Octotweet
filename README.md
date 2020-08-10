# Octoprint-OctoTweet 1.0.0

OctoTweet is a plugin allowing Octoprint to send notifications to Twitter
This is a fork of the amazing pluggin [DiscordRemote](https://plugins.octoprint.org/plugins/DiscordRemote/) by @bchanudet
![twitter result](assets/img/twitter.jpg)
![settings octoprint](assets/img/settings.jpg)
## SETUP
### Install the pluggin
Install manually using this url :  
https://github.com/jpg32/OctoPrint-Octotweet/archive/master.zip  

### Create Twitter App 
Login with your Twitter account on [Developer.twitter.com](https://developer.twitter.com/en)  
Clic to App and Create an app  
![screen twitter setup 1](assets/docs/twitter_setup_1.JPG)
Select Student  
![screen twitter setup 2](assets/docs/twitter_setup_2.JPG)
Follow the steps to complete subsciption to Twitter's Developer Program.  
![screen twitter setup 3](assets/docs/twitter_setup_3.JPG)
Now you can create a new app :  
![screen twitter setup 4](assets/docs/twitter_setup_4.JPG)
The next step show you yours API Key & API secret Key's 
![screen twitter setup 4](assets/docs/twitter_setup_5.JPG)
Put them on Octoprint-Octotweet :  
![screen octoprint 1](assets/docs/octoprint_1.JPG)
Modify app's permissions :
![screen twitter setup 6](assets/docs/twitter_setup_6.JPG)
![screen twitter setup 7](assets/docs/twitter_setup_7.JPG)
Go to *Key and tokens*  
![screen twitter setup 8](assets/docs/twitter_setup_8.JPG)
Generate *Acces Token & Secret*
![screen twitter setup 11](assets/docs/twitter_setup_11.JPG)
Copy Tokens to Octoprint :
![screen twitter setup 4](assets/docs/twitter_setup_12.JPG)
![screen twitter setup 4](assets/docs/octoprint_2.JPG)

### Message Settings

Here you can customize every message handled by Octorant.

- **Toggle the message** : by unchecking the checkbox in front of the message title, you can disable the message. It won't be sent to Twitter.
- **Message** : you can change the default content here. See the section [Message format](#message-format) for more information.
- **Include snapshot** : if you have a snapshot URL defined in the Octoprint settings, you can choose to upload a snapshot with the message to Twitter.
- **Notify every `XX`%** : specific to the `printing progress` message, this settings allows you to change the frequency of the notification :
    - `10%` means you'll receive a message at 10%, 20%, 30%, 40% ... 80%, 90% of the printing process.
    - `5%` means you'll receive a message at 5%, 10%, 15%, 20% ... 80%, 85%, 90%, 95% of the printing process.
    - etc...

### Scripts Settings

Octotweet allows you to launch scripts everytime a message is sent:

- Before sending: perfect for turning some LED on to ensure the webcam will always have enough light when taking the snapshot
- After sending: perfect for turning the same LED off :)

Script configuration was made voluntarily a little harder, as running scripts exposes much more the host computer. You can find more indications on the [wiki](https://github.com/bchanudet/OctoPrint-Octorant/wiki/Launching-scripts)

## Message format  

Messages are regular twitter messages, which means you can use :
- `:emoji:` shortcuts to display emojis
- `@mentions` to notify someone

Some events also support variables, here is a basic list :

**Printing process : started event** :
- `{name}` : file's name that's being printed
- `{path}` : file's path within its origin location
- `{origin}` : the origin storage location

**Printing process : failed event** :
- `{name}` : file's name that's being printed
- `{path}` : file's path within its origin location
- `{origin}` : the origin storage location

**Printing process : done event** :
- `{name}` : file's name that's being printed
- `{path}` : file's path within its origin location
- `{origin}` : the origin storage location
- `{time}`: time needed for the print (in seconds)
- `{time_formatted}` : same as `{time}`, but in a human-readable format (`HH:MM:SS`)

**Printing process : failed event** :                                                                                                                                                                          - `{name}` : file's name that's being printed                                                                                                                                                                  - `{path}` : file's path within its origin location
- `{origin}` : the origin storage location
- `{position}`: position of the hotend

**Printing process : paused event** :
- `{name}` : file's name that's being printed
- `{path}` : file's path within its origin location
- `{origin}` : the origin storage location
- `{position}`: position of the hotend

**Printing process : resumed event** :
- `{name}` : file's name that's being printed
- `{path}` : file's path within its origin location
- `{origin}` : the origin storage location
- `{position}`: position of the hotend

**Printing progress event** :
- `{progress}` : progress in % of the print.
- `{spent}`: time spent since the start of the print (in seconds)
- `{spent_formatted}` : same as `{spent}`, but in a human-readable format (`HH:MM:SS`)
- `{remaining}`: time remaining until the end of the print (in seconds)
- `{remaining_formatted}` : same as `{remaining}`, but in a human-readable format (`HH:MM:SS`)

**Printer state : error**
- `{error}` : The error received

For more reference, you can go to the [Octoprint documentation on Events](http://docs.octoprint.org/en/master/events/index.html#sec-events-available-events) 
