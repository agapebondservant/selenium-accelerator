FROM python:3.11-alpine

COPY requirements.txt /requirements.txt

RUN echo "http://dl-4.alpinelinux.org/alpine/v3.14/main" >> /etc/apk/repositories && \
    echo "http://dl-4.alpinelinux.org/alpine/v3.14/community" >> /etc/apk/repositories

RUN apk update
RUN apk add chromium chromium-chromedriver

RUN pip install --upgrade pip
RUN pip install selenium
RUN pip3 install -r /requirements.txt
CMD ["/bin/bash"]

