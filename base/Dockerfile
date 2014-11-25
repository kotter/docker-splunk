# Splunk
#
# using Centos 6.5, base provided via jumanjiman/puppetagent
# Using logic also found via alexanderm/docker-splunk

FROM jumanjiman/puppetagent

ADD downloads /tmp/splunk

# prereqs

# install wget
RUN yum install -y wget

# install splunk using .rpm in /tmp/splunk (staged in downloads)
RUN wget -O /tmp/splunk/splunk-6.1.5-239630-linux-2.6-x86_64.rpm 'http://www.splunk.com/page/download_track?file=6.1.5/splunk/linux/splunk-6.1.5-239630-linux-2.6-x86_64.rpm&ac=&wget=true&name=wget&platform=Linux&architecture=x86_64&version=6.1.5&product=splunk&typed=release'

# Create service
RUN /opt/splunk/bin/splunk enable boot-start --accept-license
RUN chmod 755 /etc/init.d/splunk # provides read/execute to non-root users (splunk user)
RUN chown -R splunk:splunk /opt/splunk

USER splunk

EXPOSE 8000
EXPOSE 8089
EXPOSE 9997

