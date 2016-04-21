# Agile Testing

## Part I Introduction
はじめに
### Chapter 1 What is Agile Testing
### Chapter 2 Ten Principles for Agile Testers

## Part II Organizational Challenges
組織的な課題
### Chapter 3 Cultural Challenges
### Chapter 4 Team Logistics
### Chapter 5 Transitioning Typical Processes

## Part III The Agile Testing Quadrants
アジャイルテストの四象限
### Chapter 6 The Purpose of Testing
### Chapter 7 Technology-Facing Tests that Support the Team
### Chapter 8 Business-Facing Tests that Support the Team
### Chapter 9 Toolkit for Business-Facing Tests that Support the Team
### Chapter 10 Business-Facing Tests that Critique the Product
### Chapter 11 Critiquing the Product Using Technology-Facing Tests
### Chapter 12 Summary of Testing Quadrants

## Part IV Automation
自動化について考える
### Chapter 13 Why We Want to Automate Tests and What Holds Us Back
### Chapter 14 An Agile Test Automation Strategy

## Part V An Iteration in the Life of a Tester
アジャイルに参加しているテスターのあるイテレーションの過ごし方

「テスターはテスト可能になるまでなにしてればいいの？」
アジャイルテスターがイテレーションおよび周辺でなにしてるかを説明する。
(アジャイル)テストはテスター以外のチームメンバー誰もがやるものだ。

### Chapter 15 Tester Activities in Release or Theme Planning
リリースとテーマの計画でテスターが何するか

XPチームは数ヶ月に一回リリースプランニングの日を作る(ことがある)。
その他の手法でも、テーマやエピック、主な機能といったものを事前に計画する。
実際に終わるかどうかを予測することは難しいけど、平均のベロシティを知っているので、リリースできそうなスコープをざっくり想像することはできる。
リリースプランニングをすることで、開発者や顧客に、これから出す機能が、全体システムにどんな影響を及ぼすかを知ることができる。

 - ストーリーの規模を測る
   - 手法はアジャイルな見積と計画づくりをみなはれ
   - テスト完了までの規模を出すんじゃよ
   - テスターは業務知識に詳しかったり、他システムへの影響範囲がわかったり
   - 直接開発に関係しないけどやんなきゃいけないこと(利用者トレーニングとか)も知ってたりする

ここから Connextra 形式のストーリーカードの例が出てくる。
 - Story PA-3
    - As a shopper on our site,
    - I want to delete items out of my shopping cart
    - so I don't purchase extra item that I decide I don't want

で、実際にどういう会話をするか。
 - プロダクトオーナーがカードを読み上げる
 - テスター: 一度に全部削除できちゃっていいの？
 - プロダクトオーナー: そうそう、なるべく簡単にしたいんだよね
 - テスター: 間違って買いたいもの消しちゃったらどうすんの？
 - プロダクトオーナー: 削除済みのアイテムを後々のためにとっとく方法ある？
 - プログラマ: もちろん。でもストーリーに書いてよ。今のとこは基本的な削除機能だけにしよう
 - テスター: こないだのリリースでウィッシュリスト機能出したよね。買い物カゴからウィッシュリストに移す機能も要る？これも別ストーリーにしないと。
 - プロダクトオーナー: いるね。ってことで２つストーリー追加したいことがわかった。今書くから、これも規模を見積もろう。今回のリリース無理そうなら、次のリリースに回してもいいよ。
 - テスター: この機能が引き起こしそうな最悪の事態ってなんじゃろ
 - プロダクトオーナー: ユーザーがどうやって削除したらいいかわかんないと、買い物カゴにあるもの全部を買わなくなっちゃう。だから簡単でわかりやすくしとかないと。
 - スクラムマスターが見積もりを促す。

チームはここでは削除のための最小の機能だけを作るってことを理解しているので、素早く規模を合意できる。テスターは欠けている考慮や、非機能要件についてプロダクトオーナーからいろいろ引き出していく。

次は優先順位付け。「薄いスライス」「スチールスレッド」(メアリー・ポッペンディークがいうところのMMF)。最小限必要な機能、操作パスを洗い出して、どのストーリーが必要なのかを考える。フル機能を考えることに時間を使わない。(このへんはユーザーストーリーマッピングが役に立ちそう)

優先順位付けの時に全体像がわかっていることは重要。大事なことを先にして、後回しにすることを決められる(国内配送だけを先に作る例)。不明点が多いストーリーは早めのイテレーションでやったほうがいいかもしれない。意外と時間がかかることがわかっても取り返しがつく。完了しないとまずいことになるストーリーも早めのイテレーションで。新しい技術を使わなければいけないときは、まずすんなり作れそうなのを作ってみて、あとで難しいストーリーを。新技術が自動化に影響するかもしれないので、その影響を考えると長めに時間取りたくなるかも。新しい機能はチームに時間が必要なので平均ベロシティより少なくコミットする。

テストの視点でストーリーを眺めるのは最低限必要で、テスターの腕の見せ所。チームはテスト可能なチャンクに分けたストーリーを、各イテレーションでどうこなすかを考えなければいけないので。GUIがなければテストできないことはなくて、まずアルゴリズムをテストして、そのあとでGUI込みでやったりすることもある。

エンドツーエンドの曳光弾を撃つために、テスターがまず自動化フレームワークを構築して、そのあとに個別のストーリーを考えるようにすることもある。テストが難しそうなストーリーは早めに。

リリースのデッドラインに向けて、品質を担保しながら何をスコープに残すか。価値の高いストーリーは優先順位が高い。「あったほうがいい」は後回しかも。デッドラインがある業界はたくさんあって、小売は年末商戦に、政府系は予算期に間に合わせたい。より緊急のものが出てきたら、翌年に回さないといけないものも出てくる。制度変更対応は時期をずらすわけにはいかない。

リリース計画ではユースケースを書いて確認するチャンス。ユーザーはどんなふうに機能を使って、それにどんな価値があるのか。フローチャートとか計算例なんかをホワイトボードに書いて、機能のだいじなとこを確認しよう。

アジャイルテスターは、システム全体や他システムへの影響を考える。倉庫システムをアップデートするとお店に影響が出るとか。他システムへの接点になる部分はよく考えるべき。システム間接続の絵を描く。

他社製のツールを使うときはよくテストしよう。問題が起こったときに解決まで時間がかかる。そのツールを使うために環境をアップデートしなければいけないこともあるので早めにテストを。

協力会社がリリースは自分たちの責任範囲外だと思っていることもあるので注意。また、興味深いことに、アジャイル開発をやっていないベンダーのほうがデッドラインへの準備が足りないことがある。

リリース計画では詳細なテスト計画はしない。それはイテレーション計画で行う。しかし、このリリースでどういう戦略でテストするかに時間を取るほうがいいかもしれない。アジャイルテスト四象限のうち、ビジネス面のテストを考えると、全体像を見失うのを防げるかもしれない。

テスト計画で、概要レベルのユーザー受入条件を知っておくことは役に立つ。ストーリーが曖昧だったら、テスターが具体例を聞いてみる。フローチャートや計算例をホワイトボードに書くとそのプロジェクト特有のテストの課題を議論しやすい。

テスト計画とは、リスクを軽減する戦略だ。たとえば、
 - どんな種類のテストをするのか
 - どんなインフラで、どうセットアップするか
 - テスト環境は？OSやブラウザの種類揃ってる？
 - プログラマが試せるサンドボックスある？
 - テストデータ揃ってる？本番データをもってくる？
 - 隠さなきゃいけないデータはどうする？
 - テストデータを用意するのに顧客の協力をもとめる
 - とってきたテストデータが古くなったらどうする？
 - テストデータとしてなにが必要かは継続的に見なおす
 - テスト結果をどうレポートするか？

SOX法に対応するための簡便なテスト計画シート。
テストマトリックスは縦軸にテスト対象の機能、横軸に条件を書き出してたもの。

どんなふうにテストを見える化するかも考える。アジャイルチームではテストが完了してないストーリーは完了してない、というシンプルなルールを用いることが多い。タスクボードで見えるようにする。

テストカバレッジは伝統的なメトリクス。機能数が増えた時にカバレッジが下がっていったら、その理由を調べる。テストを書きながら開発を進めればこれを避けやすい。コードカバレッジは一部に過ぎなくて、機能テストのカバレッジも忘れずに。

バグ数のメトリクスは、過去を知ることができるけど、今やっているテストの欠陥を減らすことができない。今書いているコードの欠陥をゼロにするために努力する。レガシーコードの欠陥率を調べるのは、リファクタリングや作りなおしを正当化するデータに使えるかも。

こうしたメトリクスは全体の一部にすぎなくて、ビジネスニーズを満たすかどうかがほんと大事。

### Chapter 16 Hit the Ground Running
イテレーションを始める準備



### Chapter 17 Iteration Kickoff
イテレーションの序盤
### Chapter 18 Coding and Testing
コーディングとテスティング
### Chapter 19 Wrap up the Iteration
イテレーションの終盤
### Chapter 20 Successful Delivery
デリバリーをうまくやる

## Part VI Summary
まとめ
### Chapter 21 Key Success Factors
おもな成功要因


# More Agile Testing
## PART I Introduction
はじめに
### Chapter 1 How Agile Testing Has Evolved
### Chapter 2 The Importance of Organizational Culture

## PART II Learning for Better Testing
よりよいテストをするにはどうしたらいいか
### Chapter 3 Roles and Competencies
### Chapter 4 Thinking Skills for Testing
### Chapter 5 Technical Awareness
### Chapter 6 How to Learn

## PART III Planning—So You Don’t Forget the Big Picture
計画する - 全体像を忘れないで
### Chapter 7 Levels of Precision for Planning
### Chapter 8 Using Models to Help Plan

## PART IV Testing Business Value
ビジネス価値のテスト
### Chapter 9 Are We Building the Right Thing?
### Chapter 10 The Expanding Tester’s Mindset: Is this My Job?
### Chapter 11 Getting Examples

## PART V Investigative Testing
調査系のテスト
### Chapter 12 Exploratory Testing
### Chapter 13 Other Types of Testing

## PART VI Test Automation
テスト自動化
### Chapter 14 Technical Debt in Testing
### Chapter 15 Pyramids of Automation
### Chapter 16 Test Automation Design Patterns and Approaches
### Chapter 17 Selecting Test Automation Solutions

## PART VII What Is Your Context?
あなたを取り巻く状況は？
### Chapter 18 Agile Testing in the Enterprise
### Chapter 19 Agile Testing on Distributed Teams
### Chapter 20 Agile Testing for Mobile and Embedded Systems
### Chapter 21 Agile Testing in Regulated Environments
### Chapter 22 Agile Testing for Data Warehouses and Business Intelligence Systems
### Chapter 23 Testing and DevOps

## PART VIII Agile Testing in Practice
アジャイルテストの実践
### Chapter 24 Visualize Your Testing
### Chapter 25 Putting It All Together
