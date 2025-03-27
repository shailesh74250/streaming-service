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
