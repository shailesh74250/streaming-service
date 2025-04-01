# Streaming-service
- Video call, Audio call, Schedule meeting, live meeting, live broadcasting
- Live video streaming can be implemented using WebRTC, RTMP (Real-T
- ime Messaging Protocol), or HLS (HTTP Live Streaming), depending on your use case.

## WebRTC (Best for Real-Time Video Calls, One-to-One, or Group Calls)
- Use Case: Live video consultations, video conferencing (like Zoom, Google Meet).
- Tech Stack:
 - ✅ Frontend: WebRTC API, Peer.js, React/Next.js
 - ✅ Backend: Node.js (NestJS/Express) with WebSockets (Socket.io)
 - ✅ Signaling Server: WebSockets or WebRTC SFU (Janus, Mediasoup, Jitsi)
 - ✅ TURN/STUN Server: Coturn (for NAT traversal)

Basic WebRTC Flow
User A & B establish a connection via a signaling server (WebSockets).

WebRTC negotiates video/audio streams between peers.

If direct peer-to-peer (P2P) fails, it uses a TURN server as a relay.

The connection is encrypted and low latency (sub-second).

- ✅ Pros: Real-time, low-latency, peer-to-peer communication.
- ❌ Cons: Not scalable for large audiences (use SFU like Janus for scalability).

## RTMP (Best for Large-Scale Live Streaming Like YouTube Live, Facebook Live)
- Use Case: Broadcasting live events, sports streaming, live selling (Flipkart Live).
- Tech Stack:
 - ✅ Streaming Protocol: RTMP (Real-Time Messaging Protocol)
 - ✅ Media Server: Nginx-RTMP, Ant Media Server, Wowza
 - ✅ Frontend: Video.js, HLS.js
 - ✅ CDN: AWS CloudFront, Akamai

- How RTMP Works?
 - Broadcaster (OBS, FFmpeg, Web App) sends a live stream to an RTMP server.
 - The RTMP server transcodes the stream into different resolutions (adaptive bitrate).
 - The stream is distributed using HLS (HTTP Live Streaming) for playback.
- ✅ Pros: Supports millions of viewers, optimized for broadcasting.
- ❌ Cons: Higher latency (5- 30s), needs a media server.

## HLS (Best for Video Streaming Apps like Netflix, Amazon Prime)
- Use Case: Pre-recorded and live streaming with adaptive bitrate.
- Tech Stack:
 - ✅ Video Encoding: FFmpeg
 - ✅ Storage & Distribution: AWS S3 + CloudFront
 - ✅ Frontend Player: Video.js, HLS.js

- How does HLS work?
- Video is chunked into segments (.ts files).
- A playlist file (.m3u8) tells the player how to load segments.
- Adaptive bitrate streaming ensures smooth playback even on slow networks.

- ✅ Pros: Highly scalable, works on all devices, optimized for VOD.
 - ❌ Cons: Latency (~10s), requires CDN for best performance.

## Plan HTML Video
- When to Use HLS Instead of Plain HTML Video?
  - If you need adaptive bitrate streaming (to adjust video quality based on internet speed).
  - If your video is large (e.g., 1GB+), HLS can break it into smaller chunks for smooth playback.
  - If you need Live Streaming, where HLS or WebRTC is better.


<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.</p>
    <p align="center">
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
<a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
<a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
<a href="https://opencollective.com/nest#backer" target="_blank"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
<a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-ff3f59.svg" alt="Donate us"/></a>
    <a href="https://opencollective.com/nest#sponsor"  target="_blank"><img src="https://img.shields.io/badge/Support%20us-Open%20Collective-41B883.svg" alt="Support us"></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow" alt="Follow us on Twitter"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Project setup

```bash
$ npm install
```

## Compile and run the project

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Run tests

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```

## Deployment

When you're ready to deploy your NestJS application to production, there are some key steps you can take to ensure it runs as efficiently as possible. Check out the [deployment documentation](https://docs.nestjs.com/deployment) for more information.

If you are looking for a cloud-based platform to deploy your NestJS application, check out [Mau](https://mau.nestjs.com), our official platform for deploying NestJS applications on AWS. Mau makes deployment straightforward and fast, requiring just a few simple steps:

```bash
$ npm install -g mau
$ mau deploy
```

With Mau, you can deploy your application in just a few clicks, allowing you to focus on building features rather than managing infrastructure.

## Resources

Check out a few resources that may come in handy when working with NestJS:

- Visit the [NestJS Documentation](https://docs.nestjs.com) to learn more about the framework.
- For questions and support, please visit our [Discord channel](https://discord.gg/G7Qnnhy).
- To dive deeper and get more hands-on experience, check out our official video [courses](https://courses.nestjs.com/).
- Deploy your application to AWS with the help of [NestJS Mau](https://mau.nestjs.com) in just a few clicks.
- Visualize your application graph and interact with the NestJS application in real-time using [NestJS Devtools](https://devtools.nestjs.com).
- Need help with your project (part-time to full-time)? Check out our official [enterprise support](https://enterprise.nestjs.com).
- To stay in the loop and get updates, follow us on [X](https://x.com/nestframework) and [LinkedIn](https://linkedin.com/company/nestjs).
- Looking for a job, or have a job to offer? Check out our official [Jobs board](https://jobs.nestjs.com).

## Support

Nest is an MIT-licensed open source project. It can grow thanks to the sponsors and support by the amazing backers. If you'd like to join them, please [read more here](https://docs.nestjs.com/support).

## Stay in touch

- Author - [Kamil Myśliwiec](https://twitter.com/kammysliwiec)
- Website - [https://nestjs.com](https://nestjs.com/)
- Twitter - [@nestframework](https://twitter.com/nestframework)

## License

Nest is [MIT licensed](https://github.com/nestjs/nest/blob/master/LICENSE).
