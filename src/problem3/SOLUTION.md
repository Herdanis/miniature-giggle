Provide your solution here:

## Trobleshooting

1. Disk Usage

- check overall disk usage and identify with `df -h`
- find directories consuming significant space `du -h --max-depth=1 /`

2. Check NGINX Logs

- inspect the logs size and amount both access.log and error.log in `/var/log/nginx/`
- if both of them are large consider to setup logrotate

3. Remove Unnecessary Files

- remove obsolete package using `apt-get autoremove`
- clear the package cache using`apt-get clean`

4. Check for Core Dumps

- Look in `/var/crash/` for core dump files, which can be remove

## Potential Causes and Solutions

1. Excessive NGINX Logging and Misconfiguration
   Cause: do to high traffic (possiblity DDoS) or misconfiguration lead to large of logs size
   Impact: logs consuming significant amount of disk space, potentially affecting performance
   Solution: implement log rotation to manage logs size and prevent full disk space

2. Accumulation of Unused Packages
   Cause: residual packages from updates or installations occupying space
   Impact: unnecessary disk usage, limit available of storage for essential/core operations
   Solution: do clean up unused packages and clear the package cache to free up space or better way automate using cronjob

3. Large Core Dump Files
   Cause: application crashes generate core dumps and stored on disk
   Impact: core dumps can quickly fill up storage, especially if crashes are frequent
   Solution: Analyze and resolve the root cause of crashes to prevent core dumps, remove existing dumps if they are no longer needed

## Conclustion

1. Setup the alert for all resources especially disk usage at least 80% from max capacity
2. Create the dashboard and alert for monitoring traffic if there are any anomaly or DDoS
