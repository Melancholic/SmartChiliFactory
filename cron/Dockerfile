FROM alpine:3

RUN apk upgrade -U \
 && apk add --no-cache ca-certificates ffmpeg libva-intel-driver tzdata
RUN crontab -l | { cat; echo "*/5 * * * * run-parts /etc/periodic/5min"; } | crontab -

# start crond with log level 8 in foreground, output to stderr
CMD ["crond", "-f", "-d", "8"]