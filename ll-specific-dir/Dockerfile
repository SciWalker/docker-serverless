FROM lambci/lambda:build-python3.8
COPY ./test.py /usr/app/
# RUN yum update -y && \
RUN yum install -y cairo && \
    pip3 install -t /deps_source cairosvg

CMD cp -r /deps_source/* /deps