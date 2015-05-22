# Jitsi-videobridge 
Docker container image for jitsi-videobridge daemon

Configuration options:

- VIDEOBRIDGE_SECRET (string) - secret for XEP-0114 connection to XMPP server
- XMPP_DOMAIN - XMPP domain to configure the component for (default "example.com")
- XMPP_SUBDOMAIN - XMPP subdomain for videobridge component (default "jitsi-videobridge")
- XMPP_HOST - XMPP server hostname or IP address (default "localhost")
- XMPP_PORT - port on XMPP server for XEP-0114 connections (default "5275")
- APIS - comma-separated list of APIs to enable on videobridge (as for now "xmpp" and/or "rest", default "xmpp")
- MEDIA_MIN_PORT - lowest port in a range to be exposed for media streaming (default "10000")
- MEDIA_MAX_PORT - highest port in a range to be exposed for media streaming (default "20000")

e.g.:

```
dockerun -d \
	-e XMPP_PORT=49171 \
	-e XMPP_HOST=192.168.59.103 \
	-e VIDEOBRIDGE_SECRET=AIOEfhuabeu34g8 \
	-e MEDIA_MIN_PORT=10000 \
	-e MEDIA_MAX_PORT=10020 \
	-p 50000-50020:10000-10020 jitsi-videobridge
```

will start jitsi-videobridge service for "example.com" XMPP domain, connected to XMPP server 192.168.59.103 on port 49171 (for XEP-0114), will expose media ports 10000-10020 and map to host ports 50000-50020
