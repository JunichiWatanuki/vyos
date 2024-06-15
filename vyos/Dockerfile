FROM jwat/vyos:1.5

COPY opt/vyatta/etc/config/config.boot /opt/vyatta/etc/config/
RUN chown root:vyattacfg /opt/vyatta/etc/config/config.boot

COPY initialize.sh /root/
