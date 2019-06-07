---
title: ACFの投稿オブジェクト参照で、現在の投稿と同じ言語のもののみを出力させる【Bogo・ACF】
date: 2019-06-07 18:57:11
category: Tec
tags: Bogo
---

多言語プラグインのBogoを使用していると、多言語の投稿も、普通の投稿と同じ扱いなので、
特に日本語と中国語で、タイトルが全く一緒になってどの言語か見分けがつかなくなることがあります。

このままでは利便性が悪いので、各言語の投稿に絞り込めるよう、クエリーを制御します。

# 実装

ACF側で投稿オブジェクトのクエリーを制御するフックが用意されているのでそれを使用します。
[ACF | acf/fields/post_object/query](https://www.advancedcustomfields.com/resources/acf-fields-post_object-query/)

```function.php
function my_post_object_query( $args, $field, $post_id ) {
    $locale = get_post_meta( $post_id, '_locale', true );

    $args['post_status'] = 'publish';
    $args['meta_key'] = '_locale';
    $args['meta_value'] = $locale;

    return $args;
}
add_filter('acf/fields/post_object/query', 'my_post_object_query', 10, 3);
```
↑このコード例ではすべての投稿オブジェクトに反映されます



管理画面で```get_locale()```すると、現在のユーザーが選択している言語情報で取得してしまうので、
記事に紐付いているBogoの```_locale```のカスタムフィールドを確認して、
Bogoの```meta_key```に代入し、絞り込んでいます。
