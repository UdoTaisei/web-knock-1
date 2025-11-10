# 10. HTTPとは何か調べてまとめる
## ◆ HTTPの仕組み（約200字）
WebブラウザとWebサーバ間でデータをやり取りする通信プロトコル<br>
クライアント:URLやメソッド（GET、POSTなど）を含むリクエストを送信<br>
サーバ:ステータスコードやコンテンツを含むレスポンスを返す。<br>
通信はステートレス(各リクエストが独立)<br>
Cookieやセッション、トークンなどを用いて状態管理を補完する。<br>
Webページ表示やAPI通信など、インターネット上の情報取得の基盤を担う。

## ◆ HTTPの特徴（約200字）
１回のリクエストとレスポンスで完結  
拡張性が高く、ヘッダにより機能追加が容易で、Webブラウザやサーバ間で広く採用されている。  
また、TCP上で動作し信頼性の高い接続を行う。  
ユーザ状態はCookieやセッション管理に依存する。

## ◆ HTTP/1.1・HTTP/2・HTTP/3の概要（約200字）
HTTP/1.1:従来方式で、同時並列処理に制約がある。  
HTTP/2:バイナリフレームと多重化→１つの接続で複数データを同時転送し、ヘッダ圧縮で高速化を実現する。
HTTP/3:UDPベースのQUIC→接続再確立なしの高速通信やモバイル環境での安定性


# 11. ブラウザのデベロッパーツールで通信を観察する
## Request Headers
content-type:
text/html
## Response Headers
user-agent:
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36


# 12. curlコマンドでGETリクエストを送る
## curl https://httpbin.org/get
StatusCode        : 200
StatusDescription : OK
Content           : {
                      "args": {},
                      "headers": {
                        "Host": "httpbin.org",
                        "User-Agent": "Mozilla/5.0 (Windows NT; Windows NT 10.0;
                     ja-JP) WindowsPowerShell/5.1.26100.6899",
                        "X-Amzn-Trace-Id": "Root=1-6911d...
RawContent        : HTTP/1.1 200 OK
                    Connection: keep-alive
                    Access-Control-Allow-Origin: *
                    Access-Control-Allow-Credentials: true
                    Content-Length: 304
                    Content-Type: application/json
                    Date: Mon, 10 Nov 2025 11:48:57 GM...
Forms             : {}
Headers           : {[Connection, keep-alive], [Access-Control-Allow-Origin, *],
                     [Access-Control-Allow-Credentials, true], [Content-Length,
                    304]...}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 304

## (curl https://httpbin.org/get).Content
{
  "args": {},
  "headers": {
    "Host": "httpbin.org",
    "User-Agent": "Mozilla/5.0 (Windows NT; Windows NT 10.0; ja-JP) WindowsPowerShell/5.1.26100.6899",
    "X-Amzn-Trace-Id": "Root=1-6911d217-605b59cb07d8f6c66aa60d29"
  },
  "origin": "221.240.40.206",
  "url": "https://httpbin.org/get"
}

# 13. curlコマンドでPOSTリクエストを送る