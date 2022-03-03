# Asterisk Zabbix Template

Check Asterisk PBX engine using Zabbix Network Monitoring system

**This template and scripts was originally made by InitZero and adapted to fit our needs. https://github.com/ugoviti/zabbix-templates**

## Deploy Commands

Everything is executed by only a few basic deploy scripts. 

```bash
cd /usr/local/src
git clone https://github.com/Futur-Tech/futur-tech-zabbix-asterisk.git
cd futur-tech-zabbix-asterisk

./deploy.sh 
# Main deploy script

./deploy-update.sh -b main
# This script will automatically pull the latest version of the branch ("main" in the example) and relaunch itself if a new version is found. Then it will run deploy.sh. Also note that any additional arguments given to this script will be passed to the deploy.sh script.
```

Finally import the template XML in Zabbix Server and attach it to your host.

## Features
- Easy installation and fast configuration (pure bash script without extra dependencies to install)
- Single script for discovery and checks
- Zabbix Agent based checks
- Caching of data to avoid high number of requests on asterisk engine (by default cache is valid for 60sec)
- Automatic discovery, monitoring and triggers generation for PJSIP, SIP and IAX Trunks
- Automatic discovery, monitoring and triggers generation for PJSIP, SIP and IAX Peers/Endpoints  
  (discovery of peers is enabled but items data collection is disabled by default to avoid high numbers of triggers. Selectively enable by hand the peers you want to monitor)
- Monitoring of active calls
- Monitoring of processed calls
- Monitoring of stucked calls
- Monitoring of last reload time
- Monitoring of uptime asterisk core
- Monitoring of asterisk version
- Monitoring of pjsip online/offline endpoints and registrations
- Monitoring of sip/iax2 online/offline peers and registrations
- Triggers for:
  - Max active concurrent calls
  - Call max duration time
  - Asterisk service problems
  - Asterisk restart
  - Asterisk reload
  - Asterisk version change
  - Trunks registrations problems
  - IAX2/SIP/PJSIP Peers/Endpoints unreachable
  - IAX2/SIP/PJSIP Peers/Endpoints high latency

## Template Macros available
- `{$ASTERISK_CALLS_DURATION_WARN}`: Alarm when reaching call duration time (default: 7200 seconds)
- `{$ASTERISK_CALLS_ACTIVE_WARN}`: Alarm when reaching max active calls threshold (default: 20 calls)
- `{$ASTERISK_PEER_LATENCY_WARN}`: Alarm when a peer have high latency (ms)

## BUGS
Counting SIP/PJSIP/IAX2 Trunks is not reliable right now, works only if in the trunk name is alphanumeric (contains letters and number in the name)
ex. trunk name 511123 is not recognised. trunk name terra-511123 is recognised as trunk
