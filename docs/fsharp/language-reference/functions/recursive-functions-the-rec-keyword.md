---
title: 'Yinelemeli İşlevler: rec Anahtar Sözcüğü'
description: "Bir özyinelemeli işlev tanımlamak için ' Let ' anahtar sözcüğüyle F # ' Rec ' anahtar sözcüğünün nasıl kullanıldığını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: c2374f90b4585327c6f5208a3d6bca75a23d0cbb
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455663"
---
# <a name="recursive-functions-the-rec-keyword"></a>Yinelemeli İşlevler: rec Anahtar Sözcüğü

`rec`Anahtar sözcüğü `let` özyinelemeli bir işlev tanımlamak için anahtar sözcüğüyle birlikte kullanılır.

## <a name="syntax"></a>Syntax

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a>Açıklamalar

Özyinelemeli işlevler, kendilerini çağıran işlevler, F # dilinde açıkça tanımlanır. Bu, tanımlanmakta olan tanımlayıcıların işlevin kapsamında kullanılabilir olmasını sağlar.

Aşağıdaki kod, matematik tanımını kullanarak *n*<sup>.</sup> fibonaccı numarasını hesaplayan özyinelemeli bir işlevi gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> Uygulamada, önceki örneğe benzer bir kod, unecessarily daha önce hesaplanmış olan değerleri yeniden hesaplar olduğundan ideal değildir. Bunun nedeni, bu makalede daha fazla açıklanacak tail özyinelemeli değildir.

Yöntemler tür içinde örtük olarak özyinelemeli; anahtar sözcüğü eklemeye gerek yoktur `rec` . Sınıfların içindeki bağlamaların örtülü olarak özyinelemeli olmadığından izin verin.

## <a name="tail-recursion"></a>Kuyruk özyineleme

Bazı Özyinelemeli işlevler için, daha "saf" tanımın [tail özyinelemeli](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)olan bir tanımına yeniden düzenlenmesi gerekir. Bu, gereksiz yeniden hesaplamaları önler. Örneğin, önceki fibonaccı sayı Oluşturucusu şöyle olabilir:

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

Bu daha karmaşık bir uygulama. Fibonaccı numarası oluşturmak, matematiksel olarak saf, ancak verimsiz bir "Naïve" algoritmasına yönelik harika bir örnektir. Birkaç yönü, yine de özyinelemeli olarak tanımlanmış olan F # ' da verimli hale getirir:

* Bir `loop` ı, F # deseninin adlı özyinelemeli bir iç işlev.
* İki biriktiricidir parametresi, bu değerler, çoğaltılan çağrılara biriktir.
* `n`Belirli bir birikme döndürmek için değerinin bir denetimi.

Bu örnek bir döngüyle yinelemeli olarak yazılmışsa, kod, belirli bir koşul karşılanana kadar iki farklı değer ile benzer şekilde görünür.

Bunun tail-özyinelemeli olmasının nedeni, özyinelemeli çağrının çağrı yığınında değer kaydetmesi gerekmez. Hesaplanmakta olan tüm ara değerler, iç işleve girişler aracılığıyla toplanır. Bu Ayrıca, F # derleyicisinin bir döngü gibi bir şey yazmışsınız gibi, kodu en yüksek hıza kadar hızlı bir şekilde iyileştirmelerine de olanak tanır `while` .

Önceki örnekte gösterildiği gibi, bir iç ve dış işlevle bir şeyi yinelemeli olarak işleyen F # kodu yazmak yaygındır. İç işlev, Kuyruk özyineleme kullanır, dış işlevin çağıranlar için daha iyi bir arabirimi vardır.

## <a name="mutually-recursive-functions"></a>Birbirini karşılıklı özyinelemeli Işlevler

Bazen işlevler *birbirini yinelemelidir*, yani bir işlevin bir kez çağrı yaptığı, aralarında herhangi bir sayıda çağrıya sahip olan diğeri çağıran bir daire oluşturur. Bu tür işlevleri bir bağlamada birlikte tanımlamanız gerekir `let` , `and` anahtar sözcüğünü kullanarak birbirine bağlayabilirsiniz.

Aşağıdaki örnekte birbirini dışlayan iki özyinelemeli işlev gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
