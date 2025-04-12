---
download: true
# You can also start simply with 'default'
theme: geist
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Hello TypeScript
# apply unocss classes to the current slide
# class: text-center
# https://sli.dev/features/drawing
#drawings:
  #persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
layout: cover
---

# Hello TypeScript

<br />

RUNTEQ.ts

#RUNTEQts

fujitani sora / @_fs0414

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  margin-left: 100px;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

p {
    margin-left: 100px;
    color: #ffffff;
}
</style>


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: slide-left
---

<img border="rounded" style="width: 100%; height: 100%;" src="/スクリーンショット 2025-04-12 11.27.32.png" alt="">

<!-- <style> -->
<!-- img { -->
<!--   width: 100%; -->
<!--   height: 100%; -->
<!-- } -->
<!-- </style> -->

---
transition: slide-left
---

# 注意

- TypeScriptを説明する為にRubyを引き合いに出しますが、Rubyのことは大好きですよ<br />
<br />
- 説明の為に、厳密さよりも分かりやすさを優先して資料を構成しています。<br />
  詳細が気になる方はDocmentationを参照してください。<br />
<br />
- Webアプリケーション開発の話は後の人がしてくれると思うので、自分は少し抽象的な話をします。<br />
  よって、よくわからない話が多いかもしれません。今日で全てを理解するのは無理です。<br />
  ただ、エンジニアリングというのは常に「分からなさ」との駆け引きです。<br />
  今日のイベントで得る「分からなさ」を大切に育てていってください

---
transition: slide-left 
---

# 問題：Rubyで記述された変数nameには、なんのデータ型が入るか

"mozi"（String）<br />
1（Integer）<br />
true（Boolean）


```rb
name = ?
```

<v-click>
```rb

name = "mozi"

name = 1

name = true
```

全部入る<br />
どの値でも変数に代入可能
</v-click>

<style>
h1 {
    font-size: 20px;
}
</style>

---
transition: slide-left
---

# 問題: TypeScriptで記述された変数nameには、なんのデータ型が入るか

"mozi"（String）<br />
1（Number）<br />
true（Boolean）


```typescript

let name: string = ?
```

<v-click>
```typescript

let name: string = "mozi";

let name: string = 1;
// Type 'number' is not assignable to type 'string'.

let name: string = true;
// Type 'boolean' is not assignable to type 'string'.
```
<br />

- 変数に :string を記述することで、string以外の代入がエラーになる<br />
</v-click>

---
transition: slide-left
---

# 問題：下記のコードは「StringクラスにnoImplMethodというメソッドが定義されていない」という理由でエラーになる。<br />このエラーに開発者が気づけるのはいつか

1 コードを記述したとき<br />
2 コードを実行したとき<br />

```ruby
String.noImplMethod
```
<br />

<v-click>
<br />

この答えは資料の中で...
</v-click>

---
transition: slide-left
---

# TypeScriptが解決すること

基本的に全てのツールは、なんらかの課題を解決するために誰かが作って使っている。<br />
TypeScriptが解決することは何か、なぜここまでユーザーが多いのか

---
transition: slide-left
---

# TypeScriptが解決すること

JavaScript<br />
動的型付け言語であり、GitHubが公開する言語ランキングでも毎年上位Top3に入る<br />

対照的に、よくわからん挙動が多く議論の槍玉に挙げられることも多い（諸説あり）<br />

- nullとundefind<br />
[The history of “typeof null”](1https://2ality.com/2013/10/tyeof-null.html)

- 安定しないDate（日付）の挙動
    - [Fixing JavaScript Date](https://maggiepint.com/2017/04/09/fixing-javascript-date-getting-started/)
- 暗黙的なデータ型の変換など、言語から提供されるメソッド名からは予測しずらい挙動<br />
    - 俗にいう「weakly typed（弱い型付け）」
    - [What you need to know about Javascript's Implicit Coercion](https://dev.to/promisetochi/what-you-need-to-know-about-javascripts-implicit-coercion-e23)

---
transition: slide-left
---

# TypeScriptが解決すること

> It is now common knowledge that in 1995 Brendan was given only 10 days to write the JavaScript language and get it into Netscape.<br />
[Was Javascript really made in 10 days?](https://buttondown.com/hillelwayne/archive/did-brendan-eich-really-make-javascript-in-10-days/)


> 面接ではJavaScriptの悪口をたくさん言いました。<br />
[筑波大学情報学群情報科学類を卒業した](https://sosukesuzuki.dev/posts/graduate-tsukuba-univ/#fnref2)

<br />
<v-click>
では、なぜここまでJavaScriptを使用する開発者が多いのか？🤔<br />
JavaScriptという言語の特性が関係している
</v-click>

---
transition: slide-left
---

# TypeScriptが解決すること

JavaScriptは、ブラウザ上で動作するプログラミング言語である<br />
というポイント。

Web開発者、主にFrontendはJavaScriptを避けられなかった。<br />
Frontend技術の発展もあり、複数人が関わる大規模なレポジトリをJavaScriptで運用する必要が出てくる<br />
つらい

<v-click>
これらの課題を解決するべくJavaScript言語をベースに改良や機能導入を加えたのが、TypeScriptという言語である。<br />

- 静的型付けの導入 ← 今日のポイント
- Moduleの拡張

[Ten Years of TypeScript](https://devblogs.microsoft.com/typescript/ten-years-of-typescript/)
</v-click>

<!-- --- -->
<!-- transition: slide-left -->
<!-- --- -->
<!---->
<!-- # データと型 -->
<!---->
<!-- 言語やDBには、データの単位とそれを統一的に扱うための型という概念がある。<br /> -->
<!-- データ型とは、一般的に「データの分類」を定義するものである。<br /> -->
<!---->
<!-- Ruby<br />String, Integer, Boolean ... -->
<!---->
<!-- JavaScript<br />String, Number, Boolean ... -->
<!---->
<!-- MySQL<br />String, Int, Boolean ... -->
<!---->
<!-- Rubyにおいては型という表現はされず、どのクラスのインスタンスであるかを指す -->

---
transition: slide-left
---

# 動的型付け

<!-- <div class="text-sm"> -->
<!-- TSの比較対象としてはJSが正しい気もするが「動的型付け言語」という意味では同じ挙動をするので、分かりやすさのためにRubyを例にする -->
<!-- </div> -->
<!---->
<!-- おさらい<br /> -->
<!-- Rubyには、データ型という概念がある<br /> -->
<!-- String, Integer, Boolean, Date, Array ... -->

Rubyは、コードを実行した時に初めて変数に入る値の種類が確定する言語である。<br />
動かして初めて型が決まるので「動的型付け言語」

```ruby
# Stringの値を変数nameに代入
name = "mozi"

# Stringには存在しない、noImplMethodという適当なメソッドにアクセスする
name.noImplMethod
```
<br />

エラーになるコードを記述しても、エディタは何も言わない<br />
<img class="w-80 h-15" src="/スクリーンショット 2025-04-07 16.26.16.png" alt="ローカル画像" />

---
transition: slide-left
---

# 動的型付け

```ruby
# 1p前と同じコード
# Stringの値を変数nameに代入
name = "mozi"

# Stringには存在しない、noImplMethodという適当なメソッドにアクセスする
name.noImplMethod
```

```sh
$ ruby main.rb
# => undefined method `noImplMethod' for an instance of String (NoMethodError)
```

「実行するまで、書いたコードが通るかが分からない」という特徴になる<br />
行の右辺が実行時に評価されるまで、変数nameは自分に何の値が入るかが分からない。<br />
故に、実行時にStringの値が代入されることが確定した後にしか、StringクラスにnoImplMethodがないことを判断できない。<br />

この理由で、最初に出した問題の3つ目は「実行後にしか気付けない」になる

---
transition: slide-left
---

# 静的型付け

動的型付け言語の対比として、実行前にどんな値が入るかが確定する言語を「静的型付け言語」と呼ぶ。<br />
コードを動かす前に（静的に）型が確定するので「静的型付け言語」<br />
TypeScriptは、JavaScriptをベースにした静的型付け言語に分類されます。<br />

```ts
// TypeScript
let name: string = "sora";

name.noImplMethod()
// Property 'noImplMethod' does not exist on type 'string'.
// ざっくり、string型の変数にそんな名前のメソッドは定義されていないと言われている
```

---
transition: slide-left
---

# 静的型付け


実行する前 = 記述した時点で、変数に代入できる値の種類が確定する。<br />
故に、その値に存在しないメソッドへのアクセスなどはコードを実行せずとも検知できる。<br />
それをエディタに表示することで、開発者はコードを記述した時点でエラーに気づける。<br />

<br />

<img class="w-100 h-15" src="/スクリーンショット 2025-04-07 3.19.20.png" alt="ローカル画像" />

---
transition: slide-left
---

<br />

動的型付け言語<br />
> コードを実行した時に初めて変数に入る値の種類が確定する

静的型付け言語<br />
> 記述した時点で、変数に代入できる値の種類が確定する

<br />
<img class="w-100 h-42" src="/スクリーンショット 2025-04-10 2.23.43.png" alt="ローカル画像" />

---
transition: slide-left
---

# 変数に入る値の種類

<v-click>
<h1>型</h1>
</v-click>

---
transition: slide-left
---

# 型定義

型とは、値の分類である。<br />
あらゆる文字列データは「string型」に代入できる。<br />
あらゆる数値データは「number型」に代入できる。<br />
<br />
```
number：1, 100, 2.5, -3 

string："mozi", "もじ", "السلام عليكم"

boolean：true, false

null：null

date："2025-04-10", "2025/04/10"
```

型の分類は言語毎に粒度があり、整数をInt, 小数をFloatとして扱うこともある。<br />

---
transition slide-left
---

# 型定義
TypeScritpでは、変数定義に型を記述することができる<br />
<br />
```ts
// 変数定義に型を記述することを「型注釈」 と呼ぶ
let name: string = "mozi"
let jpName: string = "もじ"
let age: number = 1

// 型注釈を記述することで、それ以外の値を代入できない状態になる
// 値に代入可能な型が確定している状態を、型が付くと表現したりする
let name: string = 1;
// Type 'number' is not assignable to type 'string'.

```
<br />

<img class="w-100 h-30" src="/スクリーンショット 2025-04-10 3.26.43.png" alt="ローカル画像" />

---
transition: slide-left
---

# 型定義

型注釈で、string型の値のみを代入できる状態を作ることで、<br />
エディタは「この変数にはstring型の値である」ことを確定できる。<br />
故に、string型の値に存在しないメソッドへのアクセスなどはエディタ上で構文エラーにできる。

```ts
let name: string = "mozi"
name.noImplMethod
// Property 'noImplMethod' does not exist on type 'string'.
```
<br />
<img class="w-100 h-15" src="/スクリーンショット 2025-04-07 3.19.20.png" alt="ローカル画像" />
<br />


値の分類を元に、変数やオブジェクトに代入可能な値を指定するのが「型を付ける」ということ。

---
transition: slide-left
---

# 型の分類

- プリミティブ型（最も基本的な型）
    - string, number, boolean, null, undefined<br />
    [プリミティブ型 (primitive types)](https://typescriptbook.jp/reference/values-types-variables/primitive-types)<br />
    ```ts
    let name: string = "mozi"
    ```

- ユーザー定義型
    - type alias, interface, enum<br />
    [型エイリアス (type alias)](https://typescriptbook.jp/reference/values-types-variables/type-alias)

```ts
type User = {
  name: string
  email: string
  arg: number
  isActive: boolean
}
```

他にも、TypeScript組み込みの型も複数存在する

---
transition: slide-left
---

# TypeScriptの3つのメリット

- コード実行以前にエラーを検出できる
- 型がドキュメントの役割を持つ
- 不正な代入の防止

---
transition: slide-left
---

# コード実行時にエラーを検出できる

これまでに話してきたこと。<br />
大規模プロジェクトになるほど、自分のコードにミスがあるかを実行しないと確認できないのはネックになる。<br />
型定義はコードの安全性だけでなく、開発者の生産性にも寄与するものである。

```ts
let name: string = "mozi"
name.noImplMethod
// Property 'noImplMethod' does not exist on type 'string'.
```

---
transition: slide-left
---

# 

# 型がドキュメントの枠割を持つ

変数や関数の働きを知りたい時に、名前と型を見れば使い方がわかるようになる。<br />
中身のロジックは、修正する時以外は読む必要がない。<br />
文脈に応じた引数を渡せばこのデータ型で値が返ってくることがわかればいい。

```ts
funciton generateSelfIntroduction(firstName: string, lastName: string. arg: number): string {
    const fullName = `${firstName} ${lastName}`
    return `私の名前は${fullName}です。${arg}歳です。`
}
```

---
transition: slide-left
---

# 不正な代入の防止

動的型付け言語では基本的にvalidationとテストコードでシステムの整合性を担保しようとする。<br />
ケースバイケースだが、テストコードの量が増えてメンテしずらいし何より毎回値の検証テストを書くのはめんどくさい<br />


```ruby
class User < ApplicationRecord
  validates :name, presence: true
end

RSpec.describe User, type: :model do
  describe 'name validation' do
    it 'nameが存在する場合は有効であること' do
      user = User.new(name: 'John Doe')
      expect(user).to be_valid
    end

    it 'nameが空の場合は無効であること' do
      user = User.new(name: nil)
      expect(user).to_not be_valid
      expect(user.errors[:name]).to include("can't be blank")
    end
  end
end
```

---
transition: slide-left
---

# 不正な代入の防止

TypeScriptは、型を付けることで不正な値が入らないコードを書くことができる。<br />
型はドキュメントであり、静的なテストでもある。<br />

外部のサービスから取得するデータの検証なども型を付けることで、値の不整合を起こさずにアプリケーションで扱うことができる。<br />
Gemから取得できる値がアップデートでstringからintegerに変わってるとか。<br />


```ts
// リクエストとレスポンスで送信できる値の整合が取れているので、不正な値でコードを書くことができない
UserRequestType = {
    name: string;
}

UserResponseType = {
    name: string;
}
``````

---
transition: slide-left
---

# 型安全

このように型を活用して、不正なコードをかけないし不正な値を入力できない「型安全」なアプリケーション開発が可能。<br />
静的型付け言語の利点である。<br />
それが動的型付け言語だがニーズの高いJavaScriptに搭載されたのがTypeScript。<br />
JavaScriptのメリットを残しつつ、型安全なアプリケーション開発が可能になる。<br />

---
transition: slide-left
---

時間が余ったら何かフリートーク

---
transition: slide-left
---

# 終わりに

今日話したことは型システムとTypeScriptの導入部分です。<br />
この後のセッションも含めて、TypeScriptという技術やコミュニティと仲良くしてくれると嬉しいです！<br />
