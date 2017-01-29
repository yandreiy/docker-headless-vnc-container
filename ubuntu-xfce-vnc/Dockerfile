FROM ubuntu:16.04

ENV DEBIAN_FRONTEND noninteractive
ENV DISPLAY :1
ENV NO_VNC_HOME /root/noVNC
ENV VNC_COL_DEPTH 24
ENV VNC_RESOLUTION 1280x1024
ENV VNC_PW vncpassword

RUN apt-get update && apt-get install -y supervisor vim xfce4 vnc4server wget && rm -rf /var/lib/apt/

EXPOSE 5901

ADD .vnc /root/.vnc
ADD scripts /root/scripts
RUN chmod +x /root/.vnc/xstartup /etc/X11/xinit/xinitrc /root/scripts/*.sh 

ENTRYPOINT ["/root/scripts/vnc_startup.sh"]
CMD ["--tail-log"]

