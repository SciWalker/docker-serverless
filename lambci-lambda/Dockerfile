FROM lambci/lambda:build-python3.8

# Based on https://aws.amazon.com/premiumsupport/knowledge-center/lambda-linux-binary-package/
RUN yum install -y yum-utils rpmdevtools
RUN yum install -y curl

WORKDIR /usr/app
COPY ./requirements.txt ./test.py /usr/app/
# RUN yum install -y cairo
ENV VIRTUAL_ENV=/usr/app/opt/venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Install dependencies:
RUN pip install -r requirements.txt

# Run the application:
CMD ["python", "test.py"]