FROM python:3.11-alpine

COPY requirements.txt /requirements.txt

RUN echo "http://dl-4.alpinelinux.org/alpine/v3.14/main" >> /etc/apk/repositories && \
    echo "http://dl-4.alpinelinux.org/alpine/v3.14/community" >> /etc/apk/repositories

RUN apk update
RUN apk add chromium chromium-chromedriver

RUN pip install --upgrade pip
RUN pip3 install -r /requirements.txt \
&& pip3 install torch~=1.7.1 -f https://download.pytorch.org/whl/torch_stable.html
CMD ["/bin/bash"]

