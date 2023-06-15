# プロバイダー ASN 早見表

誰得か分からないけど、仕事柄「プロバイダー」!=「AS 番号」ってことに気付いたので早見表を作ってみました。

例えば「楽天ひかりのユーザーが接続できない！」と言われてもサーバーログからどの ASN の公開 IP を調査すればいいのか分からないな、プロバイダーと AS 番号の早見表が出回ってたらいいのにな、と思う日々でした。

そこで「自分がその早見表を作れば良いのだ！」と気付いた結果がこれです。

（ちなみに、楽天ひかりは AS2519 アルテリアで、名称に「楽天」がある ASN ではありませんでした。）

Dunno if this will be of use to anybody, but I've noticed that when an end user mentions their ISP it doesn't really help narrow down from whence their HTTP requests might have originated.  So, an ISP <> Autonomous System Number dictionary!

## 情報を募集しています
ご自分の AS 番号と契約されているプロバイダーを下の表に追加する形でプルリクエストをすればいいんじゃないかな？

Submissions welcome.  I guess submit a pull request with your additions to the following table?

## 公開 IP アドレスと ASN を調べる方法
How to identify your public IP address and ASN

- ブラウザにてこのページにアクセス（IPv4 IPv6 双方表示）：https://www.whatismyip.com/
- curl などで ipinfo.io API を使用（IPv4 のみ）：
  ```
  $ curl ipinfo.io
  {
    "ip": "218.41.142.141",
    "hostname": "fpda298e8d.ap.nuro.jp",
    "city": "Iwaki",
    "region": "Fukushima",
    "country": "JP",
    "loc": "36.9450,140.8873",
    "org": "AS2527 Sony Network Communications Inc.",
    "postal": "971-8102",
    "timezone": "Asia/Tokyo",
    "readme": "https://ipinfo.io/missingauth"
  }$
  ```


## 表
| ISP | ASN | Sample IP 例 | Notes |
| --- | --- | --- | --- |
| [enひかり](https://enhikari.jp/) on NTT 光コラボ | AS2516 KDDI | 14.9.141.160 | NTT の光回線を使う NTT 光コラボなのに KDDI |
| ドコモ光 GMOとくとくBB | AS2516 KDDI | 106.73.5.64 | 「ドコモ」光なのに KDDI |
| Nuro 光 | AS2527 Sony Network Communications Inc. | 218.41.142.141 | |
| Nuro Mobile (MVNO) | AS2527 Sony Network Communications Inc. | 118.241.250.73 | | 
| WAKWAK | AS9595 NTT-ME Corporation | 222.224.194.212 | AS4713 NTT Communications Corporation（通称 OCN）とは別！ |
| 楽天ひかり | AS2519 ARTERIA Networks Corporation | 2001:f75:2320:700:cd32:3552:2055:537a | 名称に「Rakuten」がある ASN ではない。「クロスパス」がなんとかかんとか |
| 楽天モバイル（MNO） | AS138384 Rakuten Mobile Network, Inc | 133.106.35.20<br>240b:c010:423:e8c7:c7e3:e604:ad42:9299 | |
| 楽天モバイル（MVNO） | AS138384 Rakuten Mobile Network, Inc. | 133.106.94.244 | 2022年の記録。逆引きホスト名に「mvno」があるかで MNO・MVNO を見分ける？ |
| 楽天モバイル（MVNO） | AS4704 Rakuten Communications Corp. | 110.165.211.137 | 2018年の記録 |
| UCOM | AS17506 ARTERIA Networks Corporation | 221.248.69.179 | |
| [タイガーズネット](https://www.tigers-net.com/) | AS2519 ARTERIA Networks Corporation | 133.32.181.93 | |
| SoftBank BB | AS17676 Softbank BB Corp. | 126.142.160.144 | |
| LINEMO | AS17676 SoftBank BB Corp. | 126.211.46.133 | |
| NTT ドコモ | AS9605 NTT DOCOMO, INC. | 110.163.217.76<br>240a:6b:e40:bc11:6094:c75d:ea37:440b | |
| Starlink | AS14593 Space Exploration Technologies Corporation | 145.224.124.88 | |
| J:COM | AS4721 Jupiter Telecommunications Co., Ltd. | 203.89.39.115 | 2020年の記録 |
| JAL gogo 機内 Wi-Fi 会津若松上空 | AS4713 NTT Communications Corporation | 61.208.66.176 | 2021年11月記録 |
| JAL 機内 Wi-Fi | AS64294 Panasonic Avionics Corporation | 205.220.129.228 | 2022年2月記録 |
| JR 東北新幹線 はやぶさ車内 Wi-Fi | AS4713 NTT Communications Corporation | 210.162.55.197 | 2021年11月記録 |
| povo 2.0 | AS2516 KDDI CORPORATION | 106.128.103.50<br>2001:268:998e:2f38:b8ab:43c7:2921:995e | |
| 新千歳空港の Wi-Fi | AS4713 NTT Communications Corporation | 153.156.2.122 | |
| iCloud Private Relay「おおよその位置情報を維持」 | AS13335 Cloudflare, Inc. | 104.28.101.206 | [iCloud Private Relay で使用される IP レンジ](https://mask-api.icloud.com/egress-ip-ranges.csv) Cloudflare 以外 AS36183 Akamai なども |
| IIJMio (MVNO) | AS2497 Internet Initiative Japan Inc. | 202.214.230.88<br>2001:240:240b:24e6:d99:d972:ec6:fbca | |
| au one net | AS2516 KDDI | 106.133.121.218<br>2001:268:9a73:caa4:68d4:619a:b41f:9c2d | IPv4 ホスト名に「au-net.ne.jp」がある。 IPv6 にはない |
