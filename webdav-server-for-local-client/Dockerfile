FROM httpd
ARG path
ARG methods
ARG depthInfinity

WORKDIR /usr/local/apache2/conf
RUN [ "sed", "--in-place", "--regexp-extended", "s!^#(LoadModule (allowmethods|dav|dav_fs|dav_lock)_module modules/mod_[^/.]+\\.so|Include conf/extra/httpd-dav\\.conf)$!\\1!", "httpd.conf" ]
RUN sed --in-place --regexp-extended "s#(Alias )[^ ]+#\\1$path#; s/^( +)Dav On$/&\\n\\1DavDepthInfinity $depthInfinity/; s/(Require method ).+/\\1$methods/; s/(AuthDigestProvider|Require user) .+/#&/" extra/httpd-dav.conf

# Grant write permission from Apache to the lock file destination.
WORKDIR /usr/local/apache2
RUN [ "mkdir", "var" ]
RUN [ "chown", "daemon", "var" ]
