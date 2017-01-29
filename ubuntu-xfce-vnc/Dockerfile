FROM ubuntu:16.04

ENV DEBIAN_FRONTEND noninteractive
ENV DISPLAY :1
ENV NO_VNC_HOME /root/noVNC
ENV VNC_COL_DEPTH 24
ENV VNC_RESOLUTION 1280x1024
ENV VNC_PW vncpassword

############### xvnc / xfce installation
RUN apt-get update && apt-get install -y supervisor vim xfce4 vnc4server wget && rm -rf /var/lib/apt/

### Install noVNC - HTML5 based VNC viewer
#RUN mkdir -p $NO_VNC_HOME/utils/websockify \
    #&& wget -qO- https://github.com/ConSol/noVNC/archive/consol_1.0.0.tar.gz | tar xz --strip 1 -C $NO_VNC_HOME \
    #&&  wget -qO- https://github.com/kanaka/websockify/archive/v0.7.0.tar.gz | tar xz --strip 1 -C $NO_VNC_HOME/utils/websockify \
    #&& chmod +x -v /root/noVNC/utils/*.sh

# xvnc server porst, if $DISPLAY=:1 port will be 5901
EXPOSE 5901
# novnc web port
EXPOSE 6901

ADD .vnc /root/.vnc
ADD scripts /root/scripts
RUN chmod +x /root/.vnc/xstartup /etc/X11/xinit/xinitrc /root/scripts/*.sh 

ENTRYPOINT ["/root/scripts/vnc_startup.sh"]
CMD ["--tail-log"]

