FROM alpine:3

RUN apk upgrade -U \
 && apk add --no-cache ca-certificates ffmpeg tzdata bash coreutils findutils

RUN crontab -l | { cat; echo "*/5 * * * * /bin/bash /var/smart-chilli-factory/scripts/shots_collector"; } | crontab - \
    && crontab -l | { cat; echo "0 10 * * * /bin/bash /var/smart-chilli-factory/scripts/daily_timelapse"; } | crontab - \
    && crontab -l | { cat; echo "1 17 * * SUN /bin/bash /var/smart-chilli-factory/scripts/weekly_timelapse"; } | crontab - \
    && crontab -l | { cat; echo "1 15 9 * * /bin/bash /var/smart-chilli-factory/scripts/monthly_timelapse"; } | crontab -

# start crond with log level 8 in foreground, output to stderr
CMD ["crond", "-f", "-d", "8"]
