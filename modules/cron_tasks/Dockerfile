FROM alpine:3

RUN apk upgrade -U \
 && apk add --no-cache ca-certificates ffmpeg tzdata

RUN crontab -l | { cat; echo "*/5 * * * * /bin/sh /var/smart-chili-factory/scripts/shots_collector"; } | crontab -
RUN crontab -l | { cat; echo "0 8 * * * /bin/sh /var/smart-chili-factory/scripts/daily_timelapse"; } | crontab -

# start crond with log level 8 in foreground, output to stderr
CMD ["crond", "-f", "-d", "8"]
