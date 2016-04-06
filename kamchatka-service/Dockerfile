FROM tgregory:mcr-v81

RUN apt-get -qq install -y libxext6

RUN apt-get -qq install -y hdf5-tools

RUN apt-get -qq install -y libxt6

RUN apt-get -qq install -y libxmu6

VOLUME ["/watcher", "/data", "/output"]

COPY viirs-bin.tgz /tmp/viirs-bin.tgz

RUN cd /tmp/ \
      && tar xf viirs-bin.tgz \
      && mv viirs-bin/* /usr/local/bin \
      && rmdir viirs-bin

ENV MCROOT=/opt/mcr/v81
ENV LD_LIBRARY_PATH="$LD_LIBRARY_PATH:$MCROOT/runtime/glnxa64:$MCROOT/bin/glnxa64:$MCROOT/sys/os/glnxa64:$MCROOT/sys/java/jre/glnxa64/jre/lib/amd64/naive_threads:$MCROOT/sys/java/jre/glnxa64/jre/lib/amd64/server:$MCROOT/sys/java/jre/glnxa64/jre/lib/amd64" 


ENTRYPOINT ["/bin/sh", "-c", "/watcher/viirs-watcher /watcher/viirs-watcher-config.json > /watcher/viirs-watcher_$(date +'%Y_%m_%d_%H_%M_%S').log 2>&1"]
