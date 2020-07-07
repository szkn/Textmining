# 課題1 レポート課題
京都大学大学院情報学研究科  社会情報学専攻修士1回生  
学生番号：6930-32-1291  
鈴木賢人
  
code URL: https://github.com/szkn/textmining/day1.ipynb  
## 利用した表現手法と距離尺度
今回用いたデータセットはnltkのtwitterサンプルデータセットである。  
表現手法として、BoWとTF-IDFを用いて解析を行った。その結果、これらのベクトルの長さは87となった。 

  また距離尺度として、コサイン類似度とユークリッド距離を用いて、類似度の比較を行った。  

## 入力ドキュメントとその実行結果
今回のデータセットの具体的な内容は以下である。  
#FollowFriday @France_Inte @PKuchly57 @Milipol_Paris for being top engaged members in my community this week :)  
@Lamb2ja Hey James! How odd :/ Please call our Contact Centre on 02392441234 and we will be able to assist you :) Many thanks!  
@DespiteOfficial we had a listen last night :) As You Bleed is an amazing track. When are you in Scotland?!  
@97sides CONGRATS :)  
yeaaaah yippppy!!!  my accnt verified rqst has succeed got a blue tick mark on my fb profile :) in 15 days  
@BhaktisBanter @PallaviRuhail This one is irresistible :)  
#FlipkartFashionFriday http://t.co/EbZ0L2VENM  
We don't like to keep our lovely customers waiting for long! We hope you enjoy! Happy Friday! - LWWF :) https://t.co/smyYriipxI  
@Impatientraider On second thought, there’s just not enough time for a DD :) But new shorts entering system. Sheep must be buying.  
Jgh , but we have to go to Bayan :D bye  
As an act of mischievousness, am calling the ETL layer of our in-house warehousing app Katamari.  

そしてこれらをトークン化して解析を行い、ヒートマップとして結果をまとめた。
TF-IDFベクトル化したものをコサイン類似度で評価した。
![](2020-07-07-17-23-46.png)
BoWベクトル化したものをコサイン類似度で評価した。
![](2020-07-07-17-25-22.png)
TF-IDFをユークリッド距離の逆数で評価した。
![](2020-07-07-17-26-13.png)
BoWをユークリッド距離の逆数で評価
![](2020-07-07-17-26-49.png)

これらの結果よりコサイン類似度においては、TF-IDFベクトルで評価しても、BoWベクトルで評価してもそんなに変わらないことが分かった。  
また、ユークリッド距離に関しては二つのベクトル間で結果に差が出る結果となった。  
また、手法間の比較をしてみると、コサイン類似度とユークリッド距離の逆数の結果はあまり一致していないように感じた。  

## 結果の考察
今回の実験で考えられることは二つである。  
1.BoWベクトルでの実験でユークリッド距離の逆数が大きかったものすなわちユークリッド距離が小さかったものは、文章が短かった。これは、BoWベクトルの距離が短くなっており、距離が小さくなったのではないかと考えられる。実際、TF-IDFベクトルでのユークリッド距離は大きくなっていたことより、この仮説は有意ではないかと考える。  
2.コサイン類似度において、TF-IDFベクトルとBoWベクトルとの違いはほとんどなかった。これは、コサイン類似度はベクトルの大きさではなく二つのベクトル間の角度が関係しているからではないかと考える。

## 感想
今回テキスト分析を初めてやってみて、前処理がとても面倒であると感じた。twitterの文章を持ってきたことより、@から始まる文字や、httpなどの文字列を消す点などに留意した。またその後もとても短い文章の解析がうまくいかず、あまり有意な結果が得られなかった。次はもう少し意味のある文章でチャレンジしたいと考えている。