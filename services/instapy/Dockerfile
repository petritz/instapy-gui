FROM python:3-alpine

WORKDIR /usr/instapy

COPY . .

RUN apk add --update --no-cache --virtual .build-dependencies \
	python3-dev \
	gcc \
	musl-dev \
	g++ \
  && pip3 install -r requirements.txt \
  && pip3 uninstall -y instapy-chromedriver \
  && apk del .build-dependencies

RUN apk --update --no-cache add \
  chromium \
  chromium-chromedriver

ENV CHROMEDRIVER_PATH=/usr/bin/chromedriver
CMD ["python3", "-u", "start.py"]