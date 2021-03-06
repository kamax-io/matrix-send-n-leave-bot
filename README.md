# Matrix Send'n'Leave Bot
[![Build Status](https://travis-ci.org/kamax-matrix/matrix-send-n-leave-bot.svg?branch=master)](https://travis-ci.org/kamax-matrix/matrix-send-n-leave-bot)

---

**This project is no longer maintained.**

---

## Overview

This Matrix bot will join whatever room it is invited to, send a message, then leave.

It is designed with the following use cases in mind:
- Validate a setup, sending a "Congratulations!"-like message.
- Catch typo Matrix User IDs and send a meaningful message to the invite sender.

## Build
Requirements:
- Java JDK 1.8

```
./gradlew shadowJar
```

A runnable jar will be created in the subfolder `build/libs`

## Run
Requirements:
- Java JRE/JDK 1.8

The following environment variables are required:

| Name                | Description                                                        |
|---------------------|--------------------------------------------------------------------|
| `SNL_USER_MXISD`    | Matrix ID of the user to use for the bot.                          |
| `SNL_USER_PASSWORD` | Password of the user to use for the bot.                           |
| `SNL_HS_URL`        | Base URL of Homeserver to connect to. Auto-discovered if possible. |
| `SNL_MESSAGE`       | The message to send in rooms that the bot is invited to.           |

In the directory where the built jar is, run with:
```
<ENV>... java -jar matrix-send-n-leave-bot.jar
```

Example for:
- The user `@john:example.org`
- The password `MyPassword`
- HS Base URL is auto-discovered thanks to `.well-known` support
- Message `Hello world`

```
SNL_USER_MXID='@john:example.org' \
SNL_USER_PASSWORD='MyPassword' \
SNL_MESSAGE='Hello world' \
java -jar matrix-send-n-leave-bot.jar 
```

## Docker
Build with:
```
docker build -t matrix-send-n-leave-bot .
```

Run with:
```
docker run --rm -e 'SNL_CONFIG_KEY=...' matrix-send-n-leave-bot
```
