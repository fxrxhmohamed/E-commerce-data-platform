FROM spark:3.5.7-scala2.12-java17-python3-ubuntu

USER 0

RUN sed -i 's|http://archive.ubuntu.com/ubuntu|https://archive.ubuntu.com/ubuntu|g' /etc/apt/sources.list && \
    sed -i 's|http://security.ubuntu.com/ubuntu|https://security.ubuntu.com/ubuntu|g' /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y --no-install-recommends python3-pip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN pip3 install --no-cache-dir uv

RUN uv pip install --system --no-cache \
    pandas

RUN mkdir -p /opt/spark/.ivy2 && \
    chown -R 1000:1000 /opt/spark/.ivy2

WORKDIR /opt/spark/jobs