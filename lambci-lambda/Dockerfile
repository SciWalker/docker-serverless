FROM lambci/lambda:build-python3.8

# Based on https://aws.amazon.com/premiumsupport/knowledge-center/lambda-linux-binary-package/
RUN yum install -y yum-utils rpmdevtools
RUN yum install -y curl
WORKDIR /tmp
RUN yumdownloader --resolve \
    expat \
    glib2 \
    libffi \
    libffi-devel \
    cairo \
    pango && \
    rpmdev-extract *rpm
RUN yum install -y yum-utils libpango1.0-0
RUN yum install -y yum-utils libcairo2
RUN yum install -y yum-utils libpq-dev
RUN mkdir /opt/lib
WORKDIR /opt/lib
RUN cp -P -R /tmp/*/usr/lib64/* /opt/lib
RUN ln libgobject-2.0.so.0 libgobject-2.0.so && \
    ln libcairo.so.2 libcairo.so && \
    ln libpango-1.0.so.0 pango-1.0 && \
    ln libpangoft2-1.0.so.0 pangoft2-1.0 && \
    ln libpangocairo-1.0.so.0 pangocairo-1.0

WORKDIR /opt
RUN pip3 install jinja2 weasyprint -t python

# RUN sed -i s:/usr/share/fonts:/opt/fonts: /opt/fonts/fonts.conf

RUN zip -r /tmp/weasyprint_lambda_layer.zip \
    ./lib \
    ./python \
    ./fonts