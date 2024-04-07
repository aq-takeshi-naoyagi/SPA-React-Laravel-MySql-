# Node.jsのイメージをベースにする
FROM node:14

# アプリケーションディレクトリを設定
WORKDIR /app

# アプリケーションの依存ファイルをインストール
COPY package*.json ./
RUN npm install

# アプリケーションのソースをコピー
COPY . .

# アプリケーションを起動
CMD ["npm", "start"]
