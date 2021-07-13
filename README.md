# WeChatIRCd
## Objective
[WeChat](https://wechat.com) is the largest instant messaging platform for the Chinese nowadays. Even though it is convenient, it is still a centralized service with a large company that I do not really trust behind it.

Internet Relay Chat is a open chat protocol defined as in RFC1459. This means that on any platform, in any programming language that has basic socket libraries, a programmer can implement basic clients and servers, regardless of their license.

WeChat has only clients for Android, iOS, macOS and Windows. However, there are IRC clients written for nearly every platform out there. As mentioned above, one could easily implement IRC for a new operating system.

Mojo-Weixin and Mojo-IRCShell together form a similar experience of what I am trying to achieve. It lets the user scan a QR code with WeChat, which logs them in, then the user could connect to that computer using a normal IRC client. Then the user could use `LIST` to find the channels (group chats) they are in, etc.

Generally this works, but I find the following problems:
- Most people are *not* familiar with the Perl programming language.
- The code does not follow the conventions of writing in *any* programming language, making it a bit hard to read.
- The IRC plugin has some bad protocol violations.
	- If I do `MODE #Channel +qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM`, then that's the literal channel mode.
	- It allows having commas in nicknames and channel names, while commas are supposed to be argument separators by protocol, except if it's in the last argument prefixed with `:`.
	- It allows super long idents and hosts, making some IRC clients crash.

As a side effect, it will be easy for

## Inspiration
I have found over the past many Python libraries that may help with this project, including:
- `itchat` for a WeChat API in Python
- `omgircd3` for a Python IRC server example
- `miniirc` for a Python IRC client-bot example (written by `luk3yx` who I virtually know)
Note that since I'm writing a WeChat Client to IRC Server, `miniirc` does not *seem* that useful in this aspect. However, the project `miniirc_extras` contains information *crucial* to a client-oriented IRC server implementation: The reply numerics.
