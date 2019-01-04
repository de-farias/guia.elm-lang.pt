<!--
# An Introduction to Elm
-->
# Introdução ao Elm

<!--
**Elm is a functional language that compiles to JavaScript.** It competes with projects like React as a tool for creating websites and web apps. Elm has a very strong emphasis on simplicity, ease-of-use, and quality tooling.
-->
**Elm é uma linguagem funcional que compila para Javascript.** Ele compete com projetos como o  React para criação de páginas e aplicações web. Elm possui uma forte ênfase em simplicidade, facilidade de uso e qualidade de ferramentas.

<!--
This guide will:

  - Teach you the fundamentals of programming in Elm.
  - Show you how to make interactive apps with *The Elm Architecture*.
  - Emphasize principles and patterns that generalize to programming in any language.
-->
Este guia irá:

  - Ensinar os fundamentos para programar em Elm
  - Mostrar como fazer aplicações interativas  com _A Arquitetura Elm_ (em inglês, *The Elm Architecture*)
  - Enfatizar princípios e padrões que podem ser generalizados para programação em qualquer linguagem.

<!--
By the end I hope you will not only be able to create great web apps in Elm, but also understand the core ideas and patterns that make Elm nice to use.
-->
No final você terá a capacidade de não apenas criar boas aplicações web em Elm, mas também entender as idéias e padrões principais que fazem o Elm ser bom de se utilizar.

<!--
If you are on the fence, I can safely guarantee that if you give Elm a shot and actually make a project in it, you will end up writing better JavaScript and React code. The ideas transfer pretty easily!
-->
Se você está em cima do muro, dê uma chance e utilize Elm num projeto. É muito possível que depois disso você acabe escrevendo um código  melhor em Javascript e React. As idéias do que você vai aprender são facilmente transferíveis!

<!--
## A Quick Sample
-->

## Uma Pequena Demonstração

<!--
Of course *I* think Elm is good, so look for yourself.
-->
Claro, o Evan, criador original deste guia e também criador do Elm acha o Elm maravilhoso! Nós também achamos, e esperamos que vocês leitores também achem! Para isso, a seguir iniciaremos vendo um programa simples em Elm.

<!--
Here is [a simple counter](https://ellie-app.com/new). If you look at the code, it just lets you increment and decrement the counter:
-->
Aqui está [um simples contador](https://ellie-app.com/new). Se você olhar o código, ele permite que você incremente ou decremente o contador:

```elm
import Browser
import Html exposing (Html, button, div, text)
import Html.Events exposing (onClick)

main =
  Browser.sandbox { init = 0, update = update, view = view }

type Msg = Increment | Decrement

update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1

view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (String.fromInt model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]
```

<!--
Notice that the `update` and `view` are entirely decoupled. You describe your HTML in a declarative way and Elm takes care of messing with the DOM.
-->
Note que o `update` e a `view` são completamente desacoplados. Você escreve seu HTML de uma forma declarativa e o Elm cuida de mexer no DOM.

<!--
## Why a *functional* language?
-->
## Porquê uma linguagem funcional?

<!--
Forget what you have heard about functional programming. Fancy words, weird ideas, bad tooling. Barf. Elm is about:

  - No runtime errors in practice. No `null`. No `undefined` is not a function.
  - Friendly error messages that help you add features more quickly.
  - Well-architected code that *stays* well-architected as your app grows.
  - Automatically enforced semantic versioning for all Elm packages.
-->
まず「関数型プログラミング」について今までに聞いた話をすべて忘れてください。
なんだかよくわからない用語を使ったり、今まで見たことないような特殊な考え方だったり、実際にアプリケーションを作るのには向いていなかったり...
反吐が出ますね。

Elm はもっと実用的な以下のものを実現するために手段として関数型の考え方を使っているだけです。

  - 実用上ランタイムエラーがでないし、`null`もないし、`undefined`が関数だなんて話はありえません
  - とてもわかりやすい親切なエラーメッセージによってより素早くあなたのコードに機能を追加できます
  - コードの規模が大きくなっても全体の設計が壊れることがありません
  - すべてのElmパッケージにおいて、決められたルールに則って自動的にバージョン番号が付与されています

<!--
No combination of JS libraries can ever give you this, yet it is all free and easy in Elm. Now these nice things are *only* possible because Elm builds upon 40+ years of work on typed functional languages. So Elm is a functional language because the practical benefits are worth the couple hours you'll spend reading this guide.
-->
JSをそのまま使ったらどんなライブラリを使って工夫してもこれらを実現することはできませんが、ElmならJSという言語の枠に縛られずに簡単に実現できます。
こんな素晴らしいことが可能になるのは、Elmが「静的型付関数型言語」という40年以上の歴史を持つ研究成果を活用しているからにほかなりません。
そのためElmにとって、関数型というのは目的ではなく手段であり、こういった現実的なメリットを得るという目的のために関数型言語を採用しているに過ぎません。
もちろん関数型言語という少し見慣れないパラダイムを使っているElmを学ぶには時間が少しかかりますが、このガイドを読むのに使うたった数時間の投資に十分見合うだけの価値をもたらしてくれます。

<!--
I have put a huge emphasis on making Elm easy to learn and use, so all I ask is that you give Elm a shot and see what you think. I hope you will be pleasantly surprised!
-->
作者のEvanはElmを簡単に学んで使いはじめられるように多大な注力をしているので、Elmを少し試してみてぜひあなたの感想を教えてください。
(訳注: elm-jpでは日本語でElmについてやりとりできるdiscordを用意していますので、ぜひ[招待リンク](https://discordapp.com/invite/m9Ew6fR)から参加して感想をお聞かせください)

Elmによって楽しく新鮮な感動を覚えていただけると幸いです。
