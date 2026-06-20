# 1. 指定のベースイメージを使用
FROM python:3.13-slim

# 2. コンテナ内の作業ディレクトリを設定
WORKDIR /app

# 3. 依存関係（requirements.txt）を先にコピーしてインストール
# （キャッシュを効率よく使うためのDockerの定番手順です）
COPY requirements.txt .
RUN apt-get update && apt-get install -y --no-install-recommends \
    && pip install --no-cache-dir -r requirements.txt \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# 4. カレントディレクトリの残りのファイル（ソースコードなど）をコピー
COPY . .

# 5. 起動後に自動で bash を起動する設定
CMD ["/bin/bash"]