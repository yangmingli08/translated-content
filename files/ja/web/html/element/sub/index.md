---
title: '<sub>: 下付き文字要素'
slug: Web/HTML/Element/sub
---

{{HTMLSidebar}}

HTML の **下付き文字要素** (**`<sub>`**) は、表記上の理由で下付き文字として表示するべき行内文字列を指定します。下付き文字は普通、小さめのテキストを使用してベースラインよりも低く表示されます。

{{EmbedInteractiveExample("pages/tabbed/sub.html", "tabbed-shorter")}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/ja/docs/Web/HTML/Content_categories">コンテンツカテゴリ</a>
      </th>
      <td>
        <a href="/ja/docs/Web/HTML/Content_categories#フローコンテンツ"
          >フローコンテンツ</a
        >,
        <a href="/ja/docs/Web/HTML/Content_categories#記述コンテンツ"
          >記述コンテンツ</a
        >, 知覚可能コンテンツ
      </td>
    </tr>
    <tr>
      <th scope="row">許可されている内容</th>
      <td>
        <a href="/ja/docs/Web/HTML/Content_categories#記述コンテンツ"
          >記述コンテンツ</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">タグの省略</th>
      <td>{{no_tag_omission}}</td>
    </tr>
    <tr>
      <th scope="row">許可されている親要素</th>
      <td>
        <a href="/ja/docs/Web/HTML/Content_categories#記述コンテンツ"
          >記述コンテンツ</a
        >を受け入れるすべての要素
      </td>
    </tr>
    <tr>
      <th scope="row">暗黙の ARIA ロール</th>
      <td>
        <a href="https://www.w3.org/TR/html-aria/#dfn-no-corresponding-role"
          >対応するロールなし</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">許可されている ARIA ロール</th>
      <td>すべて</td>
    </tr>
    <tr>
      <th scope="row">DOM インターフェイス</th>
      <td>{{domxref("HTMLElement")}}</td>
    </tr>
  </tbody>
</table>

## 属性

この要素には[グローバル属性](/ja/docs/Web/HTML/Global_attributes)以外の属性はありません。

## 使用上のメモ

`<sub>` 要素は、単純に表現や表示の結果を得るためではなく、表記規則上の理由、つまり、表記上の習慣や規則でテキストの位置を変更する必要がある場合にのみ使用してください。

例えば、変更したベースラインを[ワードマーク](https://ja.wikipedia.org/wiki/ワードマーク)の中で使用している企業名にスタイル付けするために `<sub>` を使用することは適切ではありません。このような場合には CSS を使用してください (例えば {{cssxref("vertical-align")}} プロパティを、 `vertical-align: sub` または、もっと詳細にベースラインの位置を制御するために、 `vertical-align: -25%` など)。

`<sub>` の適切な利用場面には次のようなものがあります (これに限定されるものでありません)。

- 脚注番号のマークアップ。例については [Footnote numbers](#footnote_numbers) を参照してください。
- 数学における下付き文字の変数値のマークアップ（ただし、 [MathML](/ja/docs/Web/MathML) の数式を使うことも検討してください）。 [Variable subscripts](#variable_subscripts) を参照してください。
- 化学式における原子数の記述 (例えば、すべての開発者のお友達、 C8H10N4O2 別名「カフェイン」)。 [Chemical formulas](#chemical_formulas) を参照してください。

## 例

### 脚注番号

伝統的な脚注は下付き文字で表示される番号を使って記述されます。これは `<sub>` のよくある使い方です。

```html
<p>According to the computations by Nakamura, Johnson, and
Mason<sub>1</sub> this will result in the complete annihilation
of both particles.</p>
```

結果は次のようになります。

{{EmbedLiveSample("Footnote_numbers", 650, 80)}}

### 変数の下付き文字

数学では、同じ概念に関連する一連の変数 (例えば同じ軸の距離) を、同じ変数名と下付き文字を使用して表現します。例えば以下のようになります。

```html
<p>The horizontal coordinates' positions along the X-axis are
represented as <var>x<sub>1</sub></var> ... <var>x<sub>n</sub></var>.</p>
```

出力は次の通りです。

{{EmbedLiveSample("Variable_subscripts", 650, 80)}}

### 化学式

化学式を書くときは、 H20 のように、分子の記述の中で原子の数を下付き数字で記述します。水の場合、下付きの "2" は、水分子の中に 2 つの水素原子があることを表します。

他の例です。

```html
<p>ほぼすべての開発者が大好きな分子は
C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>、
「カフェイン」としてよく知られています。</p>
```

出力は次の通りです。

{{EmbedLiveSample("Chemical_formulas", 650, 120)}}

## 仕様書

| 仕様書                                                                                                                                               | 状態                             | 備考 |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- | ---- |
| {{SpecName('HTML WHATWG', 'text-level-semantics.html#the-sub-and-sup-elements', '&lt;sub&gt; and &lt;sup&gt;')}} | {{Spec2('HTML WHATWG')}} |      |
| {{SpecName('HTML5 W3C', 'textlevel-semantics.html#the-sub-and-sup-elements', '&lt;sub&gt; and &lt;sup&gt;;')}} | {{Spec2('HTML5 W3C')}}     |      |

## ブラウザーの互換性

{{Compat("html.elements.sub")}}

## 関連情報

- 上付き文字を表現する HTML の {{HTMLElement("sup")}} 要素。sub 要素と同時に使用することはできません。化学式で上付き文字と下付き文字の両方が必要な場合には、[MathML](/ja/docs/MathML) を用いる必要があります。
- MathML 要素: [`<msub>`](/ja/docs/Web/MathML/Element/msub), [`<msup>`](/ja/docs/Web/MathML/Element/msup), [`<msubsup>`](/ja/docs/Web/MathML/Element/msubsup)
- CSS の {{cssxref("vertical-align")}} プロパティ
