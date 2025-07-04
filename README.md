# MPD Client for JavaScript

[![JSR](https://jsr.io/badges/@teemukurki/mpd)](https://jsr.io/@teemukurki/mpd)

This documentation provides an overview of the MPD Client written in Deno. It
allows you to interface with an MPD (Music Player Daemon) server, enabling
control over music playback, querying the song queue, and managing the MPD
server.

## Overview

The MPD Client for Deno is a simple client that interacts with an MPD server
over a TCP socket. It is written in TypeScript using Deno, providing a modern,
secure environment to control music playback on MPD servers.

The client allows:

- Sending commands to MPD (e.g., play, pause, next, previous).
- Fetching current status and metadata about the music being played.
- Manipulating the song queue, adding or removing songs.

The client is designed to be runtime agnostic. To achieve this, we have to
separate TCP calls from the main MPD client.

## Installation

The MPD Client can be installed from JSR.

```bash
# For Deno
deno add jsr:@teemukurki/mpd # Install MPD Client
deno add jsr:@teemukurki/mpd-deno-client # Install Deno TCP client
```

```bash
# For NodeJS
npx jsr add @teemukurki/mpd # Install MPD Client
npx jsr add @teemukurki/mpd-node-client # Install NodeJS TCP client
```

## Basic usage

```typescript
import { TCPClient } from "@teemukurki/mpd-deno-client";
//import { TCPClient } from "@teemukurki/mpd-node-client"; // For NodeJS application
import { MPDClient } from "@teemukurki/mpd";

const MPD_HOST = "localhost";
const MPD_PORT = 6600;

const client = new MPDClient(
  TCPClient,
  MPD_HOST,
  MPD_PORT,
);

const status = await client.status();
console.log(status);
```
