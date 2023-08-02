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