FROM alpine

RUN apk update && apk add python3

CMD [ "8.8.8.8" ]

ENTRYPOINT [ "ping", "-t", "5" ]