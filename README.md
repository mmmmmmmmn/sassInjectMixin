# sassInjectMixin

#### before compile:

```scss
main, // 要素名のみ
.root, // クラス名のみ
#root, // id のみ
main.root, // 要素名 + クラス名
main#root, // 要素名 + id
main:first-of-type // 要素名 + 擬似クラス
    {
    >.deep {
        >.nested_1,
        >.nested_2 { {
            $target: &;

            >.selector1,
            >.selector2_1>.selector2_2,
            >.selector3_1+.selector3_2 {
                &:before {
                    // 共通のスタイル
                    display: block;
                    font-size: 20px;
                    font-weight: 700;
                    line-height: 1.5em;

                    // 個別のスタイル(ルートで分岐)
                    @include injectRoot(red_class) {
                        color: red;
                    }

                    // 個別のスタイル(途中で分岐)
                    @include inject($target, blue_class) {
                        color: blue;
                    }
                }
            }
        }
    }
}
```

#### after compile:

```css
main > .deep > .nested_1 > .selector1:before,
main > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
main > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
main > .deep > .nested_2 > .selector1:before,
main > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
main > .deep > .nested_2 > .selector3_1 + .selector3_2:before,
.root > .deep > .nested_1 > .selector1:before,
.root > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
.root > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
.root > .deep > .nested_2 > .selector1:before,
.root > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
.root > .deep > .nested_2 > .selector3_1 + .selector3_2:before,
#root > .deep > .nested_1 > .selector1:before,
#root > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
#root > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
#root > .deep > .nested_2 > .selector1:before,
#root > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
#root > .deep > .nested_2 > .selector3_1 + .selector3_2:before,
main.root > .deep > .nested_1 > .selector1:before,
main.root > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
main.root > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
main.root > .deep > .nested_2 > .selector1:before,
main.root > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
main.root > .deep > .nested_2 > .selector3_1 + .selector3_2:before,
main#root > .deep > .nested_1 > .selector1:before,
main#root > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
main#root > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
main#root > .deep > .nested_2 > .selector1:before,
main#root > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
main#root > .deep > .nested_2 > .selector3_1 + .selector3_2:before,
main:first-of-type > .deep > .nested_1 > .selector1:before,
main:first-of-type > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
main:first-of-type > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
main:first-of-type > .deep > .nested_2 > .selector1:before,
main:first-of-type > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
main:first-of-type > .deep > .nested_2 > .selector3_1 + .selector3_2:before {
    display: block;
    font-size: 20px;
    font-weight: 700;
    line-height: 1.5em;
}

main.red_class > .deep > .nested_1 > .selector1:before,
main.red_class > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
main.red_class > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
main.red_class > .deep > .nested_2 > .selector1:before,
main.red_class > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
main.red_class > .deep > .nested_2 > .selector3_1 + .selector3_2:before,
.root.red_class > .deep > .nested_1 > .selector1:before,
.root.red_class > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
.root.red_class > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
.root.red_class > .deep > .nested_2 > .selector1:before,
.root.red_class > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
.root.red_class > .deep > .nested_2 > .selector3_1 + .selector3_2:before,
#root.red_class > .deep > .nested_1 > .selector1:before,
#root.red_class > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
#root.red_class > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
#root.red_class > .deep > .nested_2 > .selector1:before,
#root.red_class > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
#root.red_class > .deep > .nested_2 > .selector3_1 + .selector3_2:before,
main.root.red_class > .deep > .nested_1 > .selector1:before,
main.root.red_class > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
main.root.red_class > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
main.root.red_class > .deep > .nested_2 > .selector1:before,
main.root.red_class > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
main.root.red_class > .deep > .nested_2 > .selector3_1 + .selector3_2:before,
main#root.red_class > .deep > .nested_1 > .selector1:before,
main#root.red_class > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
main#root.red_class > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
main#root.red_class > .deep > .nested_2 > .selector1:before,
main#root.red_class > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
main#root.red_class > .deep > .nested_2 > .selector3_1 + .selector3_2:before,
main:first-of-type.red_class > .deep > .nested_1 > .selector1:before,
main:first-of-type.red_class > .deep > .nested_1 > .selector2_1 > .selector2_2:before,
main:first-of-type.red_class > .deep > .nested_1 > .selector3_1 + .selector3_2:before,
main:first-of-type.red_class > .deep > .nested_2 > .selector1:before,
main:first-of-type.red_class > .deep > .nested_2 > .selector2_1 > .selector2_2:before,
main:first-of-type.red_class > .deep > .nested_2 > .selector3_1 + .selector3_2:before {
    color: red;
}
main > .deep > .nested_1.blue_class > .selector1:before,
main > .deep > .nested_1.blue_class > .selector2_1 > .selector2_2:before,
main > .deep > .nested_1.blue_class > .selector3_1 + .selector3_2:before,
main > .deep > .nested_2.blue_class > .selector1:before,
main > .deep > .nested_2.blue_class > .selector2_1 > .selector2_2:before,
main > .deep > .nested_2.blue_class > .selector3_1 + .selector3_2:before,
.root > .deep > .nested_1.blue_class > .selector1:before,
.root > .deep > .nested_1.blue_class > .selector2_1 > .selector2_2:before,
.root > .deep > .nested_1.blue_class > .selector3_1 + .selector3_2:before,
.root > .deep > .nested_2.blue_class > .selector1:before,
.root > .deep > .nested_2.blue_class > .selector2_1 > .selector2_2:before,
.root > .deep > .nested_2.blue_class > .selector3_1 + .selector3_2:before,
#root > .deep > .nested_1.blue_class > .selector1:before,
#root > .deep > .nested_1.blue_class > .selector2_1 > .selector2_2:before,
#root > .deep > .nested_1.blue_class > .selector3_1 + .selector3_2:before,
#root > .deep > .nested_2.blue_class > .selector1:before,
#root > .deep > .nested_2.blue_class > .selector2_1 > .selector2_2:before,
#root > .deep > .nested_2.blue_class > .selector3_1 + .selector3_2:before,
main.root > .deep > .nested_1.blue_class > .selector1:before,
main.root > .deep > .nested_1.blue_class > .selector2_1 > .selector2_2:before,
main.root > .deep > .nested_1.blue_class > .selector3_1 + .selector3_2:before,
main.root > .deep > .nested_2.blue_class > .selector1:before,
main.root > .deep > .nested_2.blue_class > .selector2_1 > .selector2_2:before,
main.root > .deep > .nested_2.blue_class > .selector3_1 + .selector3_2:before,
main#root > .deep > .nested_1.blue_class > .selector1:before,
main#root > .deep > .nested_1.blue_class > .selector2_1 > .selector2_2:before,
main#root > .deep > .nested_1.blue_class > .selector3_1 + .selector3_2:before,
main#root > .deep > .nested_2.blue_class > .selector1:before,
main#root > .deep > .nested_2.blue_class > .selector2_1 > .selector2_2:before,
main#root > .deep > .nested_2.blue_class > .selector3_1 + .selector3_2:before,
main:first-of-type > .deep > .nested_1.blue_class > .selector1:before,
main:first-of-type > .deep > .nested_1.blue_class > .selector2_1 > .selector2_2:before,
main:first-of-type > .deep > .nested_1.blue_class > .selector3_1 + .selector3_2:before,
main:first-of-type > .deep > .nested_2.blue_class > .selector1:before,
main:first-of-type > .deep > .nested_2.blue_class > .selector2_1 > .selector2_2:before,
main:first-of-type > .deep > .nested_2.blue_class > .selector3_1 + .selector3_2:before {
    color: blue;
}
```
