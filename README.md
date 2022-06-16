## WARNING / NOTES

* ___FOR REFERENCE AND EDUCATION PURPOSES ONLY. THIS DOES NOT COME WITH ANY KINDS OF WARRANTY.___

* ___PLEASE DO NOT CREATE BOTS OR DO ANY HARMFUL THINGS TO THE SERVICE. DON'T BREAK THINGS. DON'T BE EVIL.___

* ___ANDROID OFFICIAL BUILD IS OUT. THERE WILL BE NO MORE UPDATES ON THIS PROJECT.___

## Pull Requests / Issues

I disabled PRs and issues temporarily. I will only accept requests when it is worth fixing.

[Closed PRs](https://github.com/stypr/clubhouse-py/pulls?q=is%3Apr+is%3Aclosed) / [Closed Issues](https://github.com/stypr/clubhouse-py/issues?q=is%3Aissue+is%3Aclosed) 

Please contact by DMs through [@stereotype32](https://twitter.com/stereotype32) for any questions. Please do not spam e-mails for a request.

___All `rc_token` related requests will be rejected. (See closed issues)___

## QnA

> Are you affiliated with those guys who built the website that streamed Clubhouse rooms?

No.

I am not affiliated with anyone or any company with regards to Clubhouse issues.

> Why did you develop this? what is your whole intention about releasing this to public?

1. There has been a lot of articles about security concerns of Clubhouse when I joined Clubhouse.
    * [Clubhouse And Its Privacy & Security Risk](https://medium.com/technology-hits/clubhouse-and-its-security-risk-201526fd06d1)
    * [Clubhouse says it will improve security after researchers raise China spying concerns](https://www.theverge.com/2021/2/14/22282772/clubhouse-improve-security-stanford-researchers-china-security)
    * [Clubhouse: Security and privacy in the new social media app](https://blog.avast.com/clubhouse-security-and-privacy-avast)
2. I decided to take a closer look at the application by reverse engineering the app. With this I can find out what is the truth and what isn't.
3. I found some possible security risks during the analysis. However, I will not disclose this information until things are properly and safely mitigated.
4. I was planning to destroy my work after doing the analysis, but I've decided to share the code as (i) I found out that the whole authentication flow and API base may change in the future, so this src will be priceless at some point of time (ii) I think it would be better off for Android phone users to interact with others. (iii) I wanted more people to join into conversations and have fun.

> What if someone uses your code to do malicious activities? Wouldn't that be an issue?

1. Evil people with evil intentions will do bad things even if the sourcecode wasn't released.
2. There has been already numerous reports of trollers doing bad things around here and there. ([Reference](https://github.com/ai-eks/OpenClubhouse)) These trollers have also disclosed their sourcecode, so please have some time to check their source code. These guys did their stuff without even referencing other's source code. This already shows that evil people will always try to break stuff and do bad things regardless of any other helpful factors.
4. What I shared on GitHub is a very basic thing that a reverse engineer can do. It's technically not difficult to get these information snatched from the binary.
5. Clubhouse has a straightforward API with some unknown security mechanisms; They have implemented things to ban you for excessive usage.
6. DO NOT even try anything if you don't really know what you're trying to do. I have been mentioning the same message over here and there.
7. I am not liable for anything you do with this application. I already warned about this as well.

> You've released API keys and secret keys. Wouldn't that severely impact the server?

1. Let me make things clear first. Those keys are NOT confidential secrets.
2. These are just identifiers for third-party services to declare that your actions are coming from the Clubhouse app.
3. These keys are used for communication, adding your instagram/twitter accounts, chat notifications, etc.
4. I wouldn't have disclosed keys if these keys were actual secrets/confidentials.

> Can you disclose what you've found during an analysis?

No.

I will only disclose these issues to the vendor. 

I think issues I found seem to be already reported by other researchers as well and they might be already aware of these issues and circumstances.

I've already sent a twitter DM to one of Clubhouse employees as of 2021/Feb/24, but I haven't received any messages yet.

> Then, can you explain a bit on that myth about the Chinese IP thing?

1. It's fixed in the latest version. You don't have to worry about this anymore.
2. Worth reading [this technical post](https://theori.io/research/korean/analyzing-clubhouse) for more detailed information.
3. The blog post is written in Korean so please translate the page.

> I heard that the app is using iOS just to prevent the voice recording. Releasing these kinds of code can possibly make it 'easier' to make voice recording. I want to hear your opinions.

1. There is literally no way to disallow users from recording the voice. Imagine some people having a "physical" recording device next to them. How will you or the Clubhouse app detect such actions?
2. Moreover, there is no way to even catch or block the user when someone records and shares your voice record anonymously.
3. I think there are much more serious risks/problems that CH developers need to take a look at. There seem to be more high priority issues than this one. (in which I assume they're already working on atm)

> What do you think about the Clubhouse app? Is the app secure enough? Can you rate their security quality?

From my very personal perspective as a security engineer:

1. API: Well-made, and I see developers are trying to fix some security issues here. although they still haven't fixed it, yet.
2. Notifications: LGTM. but sometimes the server goes down pretty frequently. I haven't looked deep into it.
3. Interaction with voice protocol: meh, but it looks like they're trying to work on it. I think it is more fun to dig more in but doing so will go out of the scope.

> Don't you think your actions were ethically wrong?

1. I also heard that these issues were raised and discussed over several months in an open Clubhouse chatroom, and I guess I've clarified a lot of questions people had over for several months. I guess this already helped some of engineers who were pretty much concerned about things here.
2. I am pretty sure that somemone would've done this if it wasn't me anyways. At least I gave some initiative to try with good wills and share details with you guys.

> I heard that the voice communication is not encrypted. is this true?

As of 2021/Feb/24,

1. [This technical post](https://theori.io/research/korean/analyzing-clubhouse) already explains things really well about the current situation.
2. I was also curious and read some documentations in Agora.io ([Reference](https://docs.agora.io/en/Voice/channel_encryption_android))
3. As mentioned in the technical post, it looks like the communication encryption is never done. 
4. Also, ny looking at those documentations and my codes, you may have already noticed that the `enableEncryption` is never used here.
5. In the latest version, they have added the encryption routine but it is not yet used. It should be fixed in the upcoming releases.

> I heard that the app is also using Camera permissions. I am really worried right now.

You don't have to worry about this as well. There are some things to share here.

1. It may have been turned on because you tried to take a photo of yourself to put a profile image.
2. ... or the voice SDK is trying to secretly access your camera. But from my analysis, I don't see anything like that happening from the App to take photos or videos. Although they have the feature to communicate with your camera, the app does not use that part of the feature atm. (Confirmed safe as of Feb 2021)

> I heard that the app is also taking your information while adding your Instagram/Twitter accounts.  did you check that?

Yes. You don't have to worry about this as well.

Clubhouse only takes very basic part of your information just to verify that you are the owner of the given account.

* For Instagram: You're allowing Clubhouse to just take your username. That's all.
* For Twitter: You're allowing Clubhouse to read your profile, timeline and tweets. However, Clubhouse CANNOT read your personal DMs. This is the least permission they can ask to a user. 

The permission setting can also change, but in that case you will be asked again to re-authorize the application with additional permission. Don't worry so much about this part.

If you're still worried about this, You can also revoke the access by doing the following action.

* For Instagram: `Settings` -> `Security` -> `Apps and Websites` -> `Active` -> `Clubhouse` -> revoke access.
* For Twitter: `Settings` -> `Security and account access` -> `Apps and sessions` -> `Connected apps` -> `Clubhouse` -> revoke acccess.

> Do you have any plans to do further analysis if Clubhouse opens up a bug bounty programme?

Very unlikely.

> Is Clubhouse actually working hard to fix all kinds of security stuff? I'm really worried.

Yes, but there are some reasons why developers are taking some time.

1. They probably don't want to break things while updating. Developers also need time to fix and test their own code.
2. Clubhouse is a small company with ~10 employees. You also need to consider the manpower to fix issues.
3. It may take a few days to get their updates reviewed by Apple.
4. They also need to have some time to make "best moves" in order to efficiently fix issues.

> As a typical user, what do I need to be very careful about when using Clubhouse?

1. As a speaker: Always assume that someone is recording your voice. Always think multiple times before you speak. Don't speak out confidential/personal stuff. I am not saying that the Clubhouse is recording your voice. There are chances that some trolls or reporters are trying to record multiple chatrooms. 
2. As a moderator: You need to be alert and make quick decisions to make your channel healthy. If someone says something weird or does something crazy, you need to make quick decisions. Move that speaker to audience or just kick the user out of the channel. Simple as that. Also, be aware that you have a lot of privileges. Do not give moderators to unknown people. Any moderator can destroy the channel.

> Why did you block issues / PRs?

Mainly two reasons:

1. There are some people sending me some issues without actually looking into sourcecodes and testing codes.
2. There are some people wasting their time to send worthless PRs. 

I will not open these for the time being. You can send me a message or make your own fork, and I will take a look whenever I'm free

## Clubhouse API written in Python

`clubhouse-py` is originally developed for the sake of interoperability.

Standalone client is also created with very basic features, including but not limited to the audio-chat.

Please note that you may get a permanent ban for sending invalid API requests. Server's ratelimit and security mechanisms are quite strict.

## Downloads

Check [Releases](https://github.com/stypr/clubhouse-py/releases). OSX(x86_64) may not be stable for use yet.

## Demo

Please click the image to open a Youtube video demo.

[![Demo video](https://img.youtube.com/vi/1L6bEoNKego/maxresdefault.jpg)](https://www.youtube.com/watch?v=1L6bEoNKego)

## Requirements

* Windows or OSX
* Python 3.7 or higher

## Installation

### By pip 

1. Install by pip

```sh
$ pip3 install clubhouse-py
...
Successfully built clubhouse-py
Installing collected packages: clubhouse-py
Successfully installed clubhouse-py-304.0.1
```

2. You need to install Agora SDK for voice communication. Refer to [Agora-Python-SDK#installation](https://github.com/AgoraIO-Community/Agora-Python-SDK#installation).

### Manual Installation

1. Clone project

```sh
$ git clone https://github.com/stypr/clubhouse-py.git clubhouse
$ cd clubhouse
```

2. You need to install dependencies first.

```sh
$ pip3 install -r requirements.txt
```

3. You need to install Agora SDK for voice communication. Refer to [Agora-Python-SDK#installation](https://github.com/AgoraIO-Community/Agora-Python-SDK#installation).


## Usage

* For calling APIs from other script

```python
from clubhouse.clubhouse import Clubhouse

...

if __name__ == "__main__":
    clubhouse = Clubhouse()
```

* For running a standalone client

```sh
$ python3 cli.py
```

### PubNub

PubNub is used for the notification while being in a conversation.
This has not been implemented yet. However, you may utilize the PubSub keys provided in the sourcecode to implement this.

## Reference / Recommended to read

You may also add more endpoints and features based on the following repositories.

Please note that these repositories were partially referenced to create this project.

Most of things were tested and handcrafted from scratch.

* https://github.com/Seia-Soto/clubhouse-api (NodeJS build)
* https://github.com/grishka/Houseclub (Android build)
* https://theori.io/research/korean/analyzing-clubhouse/ (Written in Korean)
