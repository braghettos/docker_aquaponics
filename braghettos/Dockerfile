FROM nodered/node-red-docker:0.17.5-rpi

USER root

RUN npm install node-red-node-serialport xbee-api node-red-contrib-xbee node-red-contrib-telegrambot node-red-contrib-python-function node-red-node-twitter node-red-contrib-ibm-watson-iot node-red-contrib-play-audio

COPY ./config/flows.json /data/
COPY ./config/settings.js /data/

#RUN ls -la /data

RUN mkdir /cert

COPY ./cert/cert.pem /cert
COPY ./cert/key.pem /cert

RUN apt-get update && apt-get install -y \
        python-pip && sudo pip install requests plotly --upgrade

ENV FLOWS=/data/flows.json

#CMD ["npm", "start", "--", "--userDir", "/data", "--setting","/data/settings.js"]
