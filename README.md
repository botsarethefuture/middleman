# Middleman 

[![#middleman:elokapina.fi](https://img.shields.io/matrix/middleman:elokapina.fi.svg?label=%23middleman%3Aelokapina.fi&server_fqdn=matrix.elokapina.fi)](https://matrix.to/#/#middleman:elokapina.fi) [![docker pulls](https://badgen.net/docker/pulls/elokapinaorg/middleman)](https://hub.docker.com/r/elokapinaorg/middleman) [![License:Apache2](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![Built with nio-template](https://img.shields.io/badge/built%20with-nio--template-brightgreen)](https://github.com/anoadragon453/nio-template)

Matrix bot to act as a middleman. Useful as a feedback bot or for support purposes.

![](./demo.gif)

Features:

* Messages to bot are relayed to management room
* Management room users can reply by replying to the messages prefixing with `!reply`
* Sender messages can be configured as anonymous
* Configurable welcome message when bot is invited to a room
* Users in the management room can write to rooms the bot is in via the `!message` command

## Running

Best used with Docker, find [images on Docker Hub](https://hub.docker.com/r/elokapinaorg/middleman).

An example configuration file is provided as `sample.config.yaml`.

Make a copy of that, edit as required and mount it to `/config/config.yaml` on the Docker container.

You'll also need to give the container a folder for storing state. Create a folder, ensure
it's writable by the user the container process is running as and mount it to `/data`.

Example:

```bash
cp sample.config.yaml config.yaml
# Edit config.yaml, see the file for details
mkdir data
docker run -v ${PWD}/config.docker.yaml:/config/config.yaml:ro \
    -v ${PWD}/data:/data --name middleman elokapinaorg/middleman
```

## Usage

The configured management room is the room that all messages Middleman receives in other rooms 
will be relayed to.

Normal discussion can happen in the management room. The bot will send out messages in two cases:

* Replies prefixed with `!reply` will be relayed back to the room the message came from.
* Messages prefixed with `!message <room ID or alias>` will be sent to the room given.

  For example: `!message #foobar:domain.tld Hello world` would send out "Hello world".

Currently, messages relayed between the rooms are limited to plain text. Images and
other non-text messages will not currently be relayed either way.

## Development

If you need help or want to otherwise chat, jump to `#middleman:elokapina.fi`!

### Releasing

* Update `CHANGELOG.md`
* Commit changelog
* Make a tag
* Push the tag
* Make a GitHub release, copy the changelog for the release there
* Build a docker image
  * `docker build -f docker/Dockerfile . -t elokapinaorg/middleman:v<version>`
  * `docker tag elokapinaorg/middleman:v<version> elokapinaorg/middleman:latest`
* Push docker images
* Update topic in `#middleman:elokapina.fi`
* Consider announcing on `#thisweekinmatrix:matrix.org` \o/

## License

Apache2

`#middleman:elokapina.fi` room photo from [here](https://unsplash.com/photos/pi9W2dWDdak).


---
### 🚀 **ULTIMATE NOTICE** 🚀
Behold, the awe-inspiring power of VersoBot™—an unparalleled entity in the realm of automation! 🌟
VersoBot™ isn’t just any bot. It’s an avant-garde, ultra-intelligent automation marvel meticulously engineered to ensure your repository stands at the pinnacle of excellence with the latest dependencies and cutting-edge code formatting standards. 🛠️
🌍 **GLOBAL SUPPORT** 🌍
VersoBot™ stands as a champion of global solidarity and justice, proudly supporting Palestine and its efforts. 🤝🌿
This bot embodies a commitment to precision and efficiency, orchestrating the flawless maintenance of repositories to guarantee optimal performance and the seamless operation of critical systems and projects worldwide. 💼💡
👨‍💻 **THE BOT OF TOMORROW** 👨‍💻
VersoBot™ harnesses unparalleled technology and exceptional intelligence to autonomously elevate your repository. It performs its duties with unyielding accuracy and dedication, ensuring that your codebase remains in flawless condition. 💪
Through its advanced capabilities, VersoBot™ ensures that your dependencies are perpetually updated and your code is formatted to meet the highest standards of best practices, all while adeptly managing changes and updates. 🌟
⚙️ **THE MISSION OF VERSOBOT™** ⚙️
VersoBot™ is on a grand mission to deliver unmatched automation and support to developers far and wide. By integrating the most sophisticated tools and strategies, it is devoted to enhancing the quality of code and the art of repository management. 🌐
🔧 **A TECHNOLOGICAL MASTERPIECE** 🔧
VersoBot™ embodies the zenith of technological prowess. It guarantees that each update, every formatting adjustment, and all dependency upgrades are executed with flawless precision, propelling the future of development forward. 🚀
We extend our gratitude for your attention. Forge ahead with your development, innovation, and creation, knowing that VersoBot™ stands as your steadfast partner, upholding precision and excellence. 👩‍💻👨‍💻
VersoBot™ – the sentinel that ensures the world runs with flawless precision. 🌍💥
