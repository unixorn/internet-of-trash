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

Home Assistant has the [Works With Home Assistant](https://partner.home-assistant.io/) program that lists companies actively working with Home Assistant developers to provide the best experience for HA users. I recommend checking the integrations list and choosing from the list of [partner brands](https://www.home-assistant.io/integrations/) when buying new products to avoid unnecessary aggravation.

Support the vendors that support us.

## Hall of Shame

<!--
Please keep entries to single lines - it keeps table entries from being
corrupted when I sort the table alphabetically.

Please add new entries in alphabetical order - it will make things easier
to find when the list gets larger
-->

| Device                                       | Reason it's garbage | Date       | Workarounds if any |
| -------------------------------------------- | ------------------- | ---------- | ----------- |
| [Amysen RGBW Bulbs](https://amazon.com/gp/product/B07S2487N8/) | These WIFI smart bulbs work with Home Assistant with very little issue, however of the 10 or so I purchased over the span of about 3 months, only 3 remain in service. All the failed ones developed a driver whine (screech, really) within a short handful of months time. | 2025-08-07 | |
| [Aqara Vibration Sensor](https://amazon.com/gp/product/B07PJT939B) | This was a pita to add to my HA.<p> Once your HA is scanning for new devices, press and hold the button on the sensor for ~5 seconds until the lights flash, then you have to press it again (but don't hold it, press and release) every second or two until HA finds it.<p>Even when I did manage to add it, it kept falling off of the Zigbee mesh, even though other devices within 10 feet of it maintain stable connections. At least it was cheap. | 2025-08-07 | |
| [Aqara Water Leak Sensor](https://amazon.com/gp/product/B07D39MSZS) | Minuses - <p>The manual was unclear on how to put it in pairing mode - press the water droplet icon firmly until the hidden light flashes three times, then let go.<p>After two months of usage I don't recommend it - it drops out of my Zigbee mesh a lot, even though it's five feet from a Smartthings motion detector that has no problems.<p>Pluses - <p>These ship ready to go - no messing with the battery, just press the button and you can add it to your Zigbee mesh. | 2025-08-07 | |
| [Bambu Labs](https://bambulab.com) | Bambu announced a [firmware change](https://blog.bambulab.com/firmware-update-introducing-new-authorization-control-system-2/) that prohibits using unauthorized third-party software from controlling the printer. More details are in this [Reddit Thread](https://www.reddit.com/r/BambuLab/comments/1i3gq1t/why_you_should_care_about_bambu_labs_removing/). | 2025-01-20 | Don't upgrade your printer firmware |
| [Chamberlain](https://chamberlaingroup.com) MyQ Smart Garage Door Controller | Chamberlain shut off all access to its APIs.<br>See <ul><li>Chamberlain's [Press Release](https://chamberlaingroup.com/press/a-message-about-our-decision-to-prevent-unauthorized-usage-of-myq)</li><li>The Verge's [coverage](https://www.theverge.com/23949612/chamberlain-myq-smart-garage-door-controller-homebridge-integrations)</li></ul> | 2023-11-07 | Replace with a better solution:<ul><li>[opengarage.io](https://opengarage.io) - Their hardware design and software code (including both firmware and app code) and API documents are publicly available in the [OpenGarage github repository](https://github.com/OpenGarage)</li><li>[ratgdo](https://paulwieland.github.io/ratgdo/) is another solution with open source firmware that works with Security+ 2.0 openers.</li><li>Konnected.io [Smart Garage Door Opener](https://konnected.io/products/smart-garage-door-opener) is based on ESPHome and has an HA integration</li></ul> |
| Ariston Remotethermo | [Continuous disconnection of API](https://github.com/fustom/ariston-remotethermo-home-assistant-v3/issues/361). Not only did they break the integration, they log you out of their own crapware for as long as you're trying to use the integration. | 2024-11-15 | None. |
| Arlo Cameras | Per [reddit](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx4jo79), actively blocks attempts to access them. Uses rolling short-lived tokens to make it even more annoying to integrate. | 2024-11-15 | None |
| Astral Pool Halo Chlorinator | Per [DanielNagy/astralpool_halo_chlorinator](https://github.com/DanielNagy/astralpool_halo_chlorinator) and [community.home-assistant.io](https://community.home-assistant.io/t/viron-astral-pool-chlorinatorgo-integration/375495/408), firmware versions newer than 2.3 | 2024-11-16 | None |
| Blink Cameras | Per reddit [thread](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx4kbmd), randomly marks videos as seen in their app when connected to HA. | 2024-11-15 | None. |
| BMW | BMW turned off all 3rd party access to their APIs. See details in home assistant core [issue 149750](https://github.com/home-assistant/core/issues/149750) and on reddit at [bmw_kills_home_assistant_integration_to_protect](https://www.reddit.com/r/homeassistant/comments/1n8tidg/bmw_kills_home_assistant_integration_to_protect/) |  2025-09-10 | |
| Ecobee thermostats | "As of March 28th, 2024, ecobee is no longer accepting new developer subscriptions, nor are existing developer accounts able to create new API keys. There is no ETA for when they will be allowed again. Existing API keys will continue to function." | 2024-11-15 | Their HomeKit integration still works, so your HA can connect via that. It's less robust than a real connection, though. |
| Eight Sleep Beds | Locked part of the API behind a paywall. | 2024-11-15 | Lucas Clarke's [integration](https://github.com/lukas-clarke/eight_sleep). Subject to breakage if they change their API again.  |
| Eufy cameras | Per [reddit](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx4jo79), the community integration is hit or miss due to flakiness on the Eufy side. Disables RTSP if you don't let it phone home for more than 48 hours. Requires disabling a bunch of security stuff to access the RTSP stream even when it _does_ work. | 2024-11-15 | None |
| GM OnStar | GM changes or voids API keys, which makes it really hard for the integration developers to keep up. | 2024-11-15 | [OnStar JS](https://github.com/samrum/OnStarJS) is an unofficial NodeJS library to make OnStar requests. Instability is because the devs have to chase GM changes. |
| iRobot Roomba j7 | Per [reddit](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx4d50k), cannot be added directly through the HA integration. [Firmware version 3.20.7 stopped reporting tracking and broke realtime maps.](https://github.com/NickWaterton/Roomba980-Python) | 2024-11-14 | Reportedly you can use [koalazak/dorita980](https://github.com/koalazak/dorita980) to hack it into compliance, but it doesn't work with the stock roomba integration |
| Jaguar / Land Rover | Per [reddit](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx511wu/), they've changed their API authentication and broken API access. | 2024-11-15 | None |
| Kasa light bulbs | The KL135 (and probably others) reset themselves every 10 minutes if their internet is blocked, which makes them go offline for a minute during the reset. | 2024-11-15 | Let them phone home. |
| Kasa smart plugs | EP25 plugs won't do energy monitoring without internet access. For details, see this [reddit thread](https://www.reddit.com/r/homeassistant/comments/1htfj0h/caution_against_kasa_smart_plugs/). | None |
| Mazda | The Home Assistant Blog has the [details](https://www.home-assistant.io/blog/2023/10/13/removal-of-mazda-connected-services-integration/).<br>TL;DR they sent a cease and desist order to the Mazda Home Assistant Integration's author. | 2023-11-09 | None |
| Ooma VOIP | No API, no integration. | 2024-11-15 | None |
| Philips Hue | Philips is forcing users to "upgrade" to a version of their Philips app that requires login to a cloud account. See [How-To Geek](https://www.howtogeek.com/philips-hue-will-soon-require-online-accounts-to-control-lights/) | 2023-11-07 | Use a generic Zigbee coordinator instead of the Philips one |
| RecTeq Smokers | Tuya based, but per [reddit](https://www.reddit.com/r/homeassistant/comments/1graane/comment/lx56e3x), they pushed an update that locked people out of their smokers. | 2024-11-15 | None |
| Shark Vacuums | Shark has altered the API and broken the SharkIQ integration. See [sharkiq/issues/51](https://github.com/JeffResc/sharkiq/issues/51). This is an vendor problem, please don't harass the sharkiq maintainer. | 2024-11-14 | None |
| Tesla (Powerwall) | Tesla have updated their gateway firmware to progressively hobble it, reducing the ability for owners to monitor their devices.  This has reached peak enshittification with firmware version 24.36.2 and later with Gateway 1 vintage gateways.  Although you can temporarily gain access by going through the _I forgot my password_ routine via the Tesla Energy Gateway (TEG) WiFi access point, and log in to the integration in Home Assistant immediately with the new password, **the gateway itself forgets the new password** within an hour, and once the login cookie expires, any logged in device loses access.  | 2024-02-02 | Tesla Fleet provides a dramatically reduced subset of information |
| Tesla | Tesla is now [Charging for API access](https://developer.tesla.com/docs/fleet-api/billing-and-limits) to the vehicle API. They're adding a new Fleet API that costs money to use. The Owner API is working for now, but it's unclear when/if support for it is going to be dropped. | 2024-12-15 | None |
| Wyze Cameras | Wyze used to have a RTSP firmware which worked well (I have one) but then they abandoned it. | 2024-11-15 | [Thingino](https://thingino.com/) has some open source firmwares which may work. Additionally, the [wz_mini_hacks](https://github.com/gtxaspec/wz_mini_hacks) firmware works well with many of their cameras. |

## Reformed

These vendors were in the Hall of Shame but have worked with the community to re-enable lost functionality.

| Device                                       | How they reformed | Date       | Workarounds if any |
| -------------------------------------------- | ------------------- | ---------- | ----------- |
| Genie Aladdin Connect | Now have a Python SDK for  their API, [Genie-Garage/aladdin-python-sdk](https://github.com/Genie-Garage/aladdin-python-sdk). This requires that your opener have internet access| 2025-06-16 | If you don't want to grant the opener access to the internet, there are two add-on solutions to smarten the opener:<ul><li>[opengarage.io](https://opengarage.io) - Their hardware design and software code (including both firmware and app code) and API documents are publicly available in the [OpenGarage github repository](https://github.com/OpenGarage)</li><li>[ratgdo](https://paulwieland.github.io/ratgdo/) is another solution with open source firmware that works with Security+ 2.0 openers.</li><li>Konnected.io [Smart Garage Door Opener](https://konnected.io/products/smart-garage-door-opener) is based on ESPHome and has an HA integration</li></ul> |
| Haier Europe | Haier Europe is now working with the HON developer - see his [timeline](https://github.com/Andre0512/hon/blob/main/takedown_timeline.md). | 2024-01-18 | Update to v0.12.0 or later to include the polling changes requested by Haier Europe. |


## Contributors

<a href="https://github.com/unixorn/internet-of-trash/graphs/contributors">
  <img src="https://contributors-img.web.app/image?repo=unixorn/internet-of-trash" />
</a>

Made with [contributors-img](https://contributors-img.web.app).
