# Docker Hubにあるpythonイメージをベースにする
FROM python:3.6-alpine

# 環境変数を設定する
ENV PYTHONUNBUFFERED 1

# コンテナ内にcodeディレクトリを作り、そこをワークディレクトリとする
RUN mkdir /code
WORKDIR /code

# プロジェクトソースコードをcodeディレクトリにコピーする
ADD ./portfolio /code/

# --update(インストール可能なパッケージ一覧の更新)オプションを付けるとエラー解消される 
# --virtual(グルーピングしてまとめて削除)
# 他も調べる
RUN apk update && \
    apk upgrade && \
    apk --no-cache add --update --virtual=.build-dependencies \
      build-base \
      postgresql-dev \
      jpeg-dev zlib-dev libjpeg && \
    apk --no-cache add --update \
      git \
      bash \
      libpq && \
    pip install --upgrade pip && \
    pip install -r requirements.txt
    # apk del .build-dependencies 今のまま消すと動作しなくなるから仮コメント