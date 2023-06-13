FROM ubuntu:22.04
USER root

COPY requirements.txt /requirements.txt

RUN export DEBIAN_FRONTEND=noninteractive \
&& apt-get update -y \
&& apt-get install -y --no-install-recommends software-properties-common gpg-agent lsb-core python3-pip \
&& echo "deb [trusted=yes] https://apt.postgresml.org $(lsb_release -cs) main" >> /etc/apt/sources.list \
&& add-apt-repository ppa:deadsnakes/ppa \
&& apt install -y --no-install-recommends unzip xvfb libxi6 libgconf-2-4 python3.11 curl default-jdk \
&& curl -sS -o - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add \
&& bash -c "echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' >> /etc/apt/sources.list.d/google-chrome.list" \
&& apt-get update -y \
&& apt -y install --no-install-recommends google-chrome-stable \

&& /bin/sh -c wget -O /tmp/chromedriver.zip http://chromedriver.storage.googleapis.com/`curl -sS chromedriver.storage.googleapis.com/LATEST_RELEASE`/chromedriver_linux64.zip \
# wget $(echo "https://chromedriver.storage.googleapis.com/114.0.5735.90/chromedriver_linux64.zip") \
# && unzip chromedriver_linux64.zip chromedriver -d /usr/local/bin \
&& unzip /tmp/chromedriver.zip chromedriver -d /usr/local/bin/ \
&& chown root:root /usr/local/bin/chromedriver \
&& chmod +x /usr/local/bin/chromedriver \
&& apt-get clean \
&& rm -rf /var/lib/apt/lists/*

RUN pip3 install -r /requirements.txt

USER selenium

CMD ["/bin/bash"]

