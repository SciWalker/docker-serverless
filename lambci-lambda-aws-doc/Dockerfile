FROM lambci/lambda:build-python3.8

# Based on https://aws.amazon.com/premiumsupport/knowledge-center/lambda-linux-binary-package/
RUN yum install -y yum-utils rpmdevtools
RUN yum install -y curl

WORKDIR /usr/app
COPY . "/usr/app"
RUN yum install -y cairo 

# RUN yum install -y cairo
# ENV VIRTUAL_ENV=/usr/app/opt/venv
# RUN python3 -m venv $VIRTUAL_ENV
# ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Install dependencies:
RUN pip install \
    --platform manylinux2014_x86_64 \
    --target=usr/app \
    --implementation cp \
    --python 3.8 \
    --only-binary=:all: --upgrade \
    cairosvg

# Run the application:
# CMD ["python", "test.py"]
# RUN python test.py