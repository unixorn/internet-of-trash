# Internet-of-Trash

![Awesomebot](https://github.com/unixorn/internet-of-trash/actions/workflows/awesomebot.yml/badge.svg)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table of Contents

- [Works With Home Assistant](#works-with-home-assistant)
- [Hall of Shame](#hall-of-shame)
- [Reformed](#reformed)
- [Contributors](#contributors)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

A list of IOT devices to avoid.

Some of the reasons things get listed here:

- A device had an open API, then switched to requiring you to use their application instead of directly scraping the API
- Devices which are cloud-only
- Anything that requires you to use _their_ application and doesn't document their API so it can be integrated with other ecosystems

## Works With Home Assistant

Home Assistant has the [Works With Home Assistant](https://partner.home-assistant.io/) program that lists companies actively working with Home Assistant the developers to provide the best experience for HA users. I recommend checking the integrations list and choosing [partner brands](https://www.home-assistant.io/integrations/) to see the current list when buying new products.

Support the vendors that support us.

## Hall of Shame

<!--
Please keep entries to single lines - it makes sorting them much easier
Please add new entries in alphabetical order - it will make things easier to find when the list gets larger
-->

| Device                                       | Reason it's garbage | Date       | Workarounds if any |
| -------------------------------------------- | ------------------- | ---------- | ----------- |
| Ariston Remotethermo | [continuous disconnection of API](https://github.com/fustom/ariston-remotethermo-home-assistant-v3/issues/361). Not only did they break the integration, they log you out of their own crapware for as long as you're trying to use the integration. | 2024-11-15 | None. |
| Arlo Cameras | Per [reddit](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx4jo79) actively blocks attempts to access them. Uses rolling short-lived tokens to make it even more annoying to integrate. | 2024-11-15 | None |
| Astral Pool Halo Chlorinator | Per [DanielNagy/astralpool_halo_chlorinator](https://github.com/DanielNagy/astralpool_halo_chlorinator) and [community.home-assistant.io](https://community.home-assistant.io/t/viron-astral-pool-chlorinatorgo-integration/375495/408), firmware versions newer than 2.3 | 2024-11-16 | None |
| Blink Cameras | Per reddit [thread](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx4kbmd), randomly marks videos as seen in their app when connected to HA | 2024-11-15 | None. |
| Chamberlain MyQ Smart Garage Door Controller | Chamberlain shut off all access to its APIs.<br>See <ul><li>Chamberlain's [Press Release](https://chamberlaingroup.com/press/a-message-about-our-decision-to-prevent-unauthorized-usage-of-myq)</li><li>The Verge's [coverage](https://www.theverge.com/23949612/chamberlain-myq-smart-garage-door-controller-homebridge-integrations)</li></ul> | 2023-11-07 | Replace with a better solution:<ul><li>[opengarage.io](https://opengarage.io) - Their hardware design and software code (including both firmware and app code) and API documents are publicly available in the [OpenGarage github repository](https://github.com/OpenGarage)</li><li>[ratgdo](https://paulwieland.github.io/ratgdo/) is another solution with open source firmware that works with Security+ 2.0 openers.</li><li>Konnected.io [Smart Garage Door Opener](https://konnected.io/products/smart-garage-door-opener) is based on ESPHome and has an HA integration</li></ul> |
| Ecobee thermostats | "As of March 28th, 2024, ecobee is no longer accepting new developer subscriptions, nor are existing developer accounts able to create new API keys. There is no ETA for when they will be allowed again. Existing API keys will continue to function." | 2024-11-15 | Their HomeKit integration still works, so your HA can connect via that. It's less robust than a real connection, though. |
| Eight Sleep Beds | Locked part of the API behind a paywall. | 2024-11-15 | Lucas Clarke's [integration](https://github.com/lukas-clarke/eight_sleep). Subject to breakage if they change their API again.  |
| Eufy cameras | Per [reddit](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx4jo79), the community integration is hit or miss due to flakiness on the Eufy side. Disables RTSP if you don't let it phone home for more than 48 hours. Requires disabling a bunch of security stuff to access the RTSP stream even when it _does_ work. | 2024-11-15 | None |
| Genie Aladdin Connect | Removed their API access citing licensing issues, supposedly a fix is on the way, but it's been months now and they seem to be letting it [die quietly](https://www.reddit.com/r/homeassistant/comments/1dutam5/aladdin_connect_integration_removed/) | 2024-07-02 | If you don't want to replace the opener, there are two add-on solutions to smarten the opener:<ul><li>[opengarage.io](https://opengarage.io) - Their hardware design and software code (including both firmware and app code) and API documents are publicly available in the [OpenGarage github repository](https://github.com/OpenGarage)</li><li>[ratgdo](https://paulwieland.github.io/ratgdo/) is another solution with open source firmware that works with Security+ 2.0 openers.</li><li>Konnected.io [Smart Garage Door Opener](https://konnected.io/products/smart-garage-door-opener) is based on ESPHome and has an HA integration</li></ul> |
| GM OnStar | GM changes or voids API keys, which makes it really hard for the integration developers | 2024-11-15 | [OnStar JS](https://github.com/samrum/OnStarJS) is an unofficial NodeJS library to make OnStar requests. Instability is because the devs have to chase GM changes. |
| iRobot Roomba j7 | Per [reddit](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx4d50k), cannot be added directly through the HA integration. [Firmware version 3.20.7 stopped reporting tracking and broke realtime maps.](https://github.com/NickWaterton/Roomba980-Python) | 2024-11-14 | Reportedly you can use [koalazak/dorita980](https://github.com/koalazak/dorita980) to hack it into compliance, but it doesn't work with the stock roomba integration |
| Jaguar / Land Rover | Per [reddit](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx511wu/), they've changed their API authentication and broken API access | 2024-11-15 | None |
| Kasa light bulbs | The KL135 (and probably others) reset themselves every 10 minutes if their internet is blocked, which makes them go offline for a minute during the reset | 2024-11-15 | Let them phone home. |
| Mazda. Yes, Mazda. | The Home Assistant Blog has the [details](https://www.home-assistant.io/blog/2023/10/13/removal-of-mazda-connected-services-integration/).<br>TL;DR they sent a cease and desist order to the Mazda Home Assistant Integration's Author | 2023-11-09 | None |
| Ooma VOIP | No API, no integration. | 2024-11-15 | None |
| Philips Hue | Philips is forcing users to "upgrade" to a version of their Philips app that requires login to a cloud account. See [How-To Geek](https://www.howtogeek.com/philips-hue-will-soon-require-online-accounts-to-control-lights/) | 2023-11-07 | Use a generic Zigbee coordinator instead of the Philips one |
| RecTeq Smokers | Tuya based, but per [reddit](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx56e3x), they pushed an update that locked people out of their smokers | 2024-11-15 | None |
| Shark Vacuums | Shark has altered the API and broken the SharkIQ integration. See [sharkiq/issues/51](https://github.com/JeffResc/sharkiq/issues/51). This is an vendor problem, please don't harass the sharkiq maintainer. | 2024-11-14 | None |
| Wyze Cameras | Wyze used to have a RTSP firmware which worked well (I have one) but then they abandoned it. | 2024-11-15 | [Thingino](https://thingino.com/) has some open source firmwares which may work. Additionally, the [wz_mini_hacks](https://github.com/gtxaspec/wz_mini_hacks) firmware works well with many of their cameras. |

## Reformed

These vendors were in the Hall of Shame but have worked with the community to re-enable lost functionality.

| Device                                       | How they reformed | Date       | Workarounds if any |
| -------------------------------------------- | ------------------- | ---------- | ----------- |
| Haier Europe | Haier Europe is now working with the HON developer - see his [timeline](https://github.com/Andre0512/hon/blob/main/takedown_timeline.md). | 2024-01-18 | Update to v0.12.0 or later to include the polling changes requested by Haier Europe. |

## Contributors

<a href="https://github.com/unixorn/internet-of-trash/graphs/contributors">
  <img src="https://contributors-img.web.app/image?repo=unixorn/internet-of-trash" />
</a>

Made with [contributors-img](https://contributors-img.web.app).
