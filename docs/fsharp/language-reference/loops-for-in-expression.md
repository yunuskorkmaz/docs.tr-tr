---
title: 'Döngüler: for...in İfadesi'
description: F# İçin bkz.... ifade döngüsü yapısı, sıralanabilir bir koleksiyondaki bir düzenin eşleşmelerini yinelemek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 640b0f91f6c641f3b49a99dc67abe7e4c31911ea
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630720"
---
# <a name="loops-forin-expression"></a>Döngüler: for...in İfadesi

Bu döngü yapısı, bir Aralık ifadesi, sırası, liste, dizi ya da numaralandırmayı destekleyen diğer yapı gibi sıralanabilir bir koleksiyondaki bir düzenin eşleşmelerini yinelemek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Açıklamalar

İfade, sıralanabilir bir koleksiyondaki değerleri döngüye `for each` almak için kullanıldığından, diğer .net dillerdeki deyimle karşılaştırılabilir. `for...in` Bununla birlikte `for...in` , yalnızca tüm koleksiyon üzerinde yineleme yerine koleksiyon üzerinde model eşleştirmeyi de destekler.

Sıralanabilir ifade, sıralanabilir bir koleksiyon olarak veya `..` işleç kullanılarak integral türünde bir Aralık olarak belirtilebilir. Sıralanabilir koleksiyonlar listeler, sıralar, diziler, kümeler, haritalar vb. içerir. Uygulayan `System.Collections.IEnumerable` herhangi bir tür kullanılabilir.

`..` İşlecini kullanarak bir Aralık ifade ettiğinizde, aşağıdaki sözdizimini kullanabilirsiniz.

*Başlat* .. *sona*

Aşağıdaki kodda olduğu gibi, *Atla*adlı bir artış içeren bir sürüm de kullanabilirsiniz.

*Başlat* .. *Atla* .. *sona*

Model olarak integral aralıklar ve basit bir sayaç değişkeni kullandığınızda, tipik davranış her yinelemede Sayaç değişkenini 1 artırır, ancak Aralık bir atlama değeri içeriyorsa, sayaç atlama değeri ile artırılır.

Düzende eşleşen değerler de gövde ifadesinde kullanılabilir.

Aşağıdaki kod örnekleri, `for...in` ifadesinin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

Çıktı aşağıdaki gibidir:

```
1
5
100
450
788
```

Aşağıdaki örnek, bir sıranın üzerinde nasıl döngü yapılacağını ve basit bir değişken yerine demet deseninin nasıl kullanılacağını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

Çıktı aşağıdaki gibidir:

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

Aşağıdaki örnek, bir basit tamsayı aralığının nasıl ekleneceğini gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

İşlev1 çıkışı aşağıdaki gibidir.

```
1 2 3 4 5 6 7 8 9 10
```

Aşağıdaki örnek, aralığın her bir öğesini de içeren, bir Aralık üzerinde döngünün nasıl ekleneceğini gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

Çıkışı `function2` aşağıdaki gibidir.

```
1 3 5 7 9
```

Aşağıdaki örnek, bir karakter aralığının nasıl kullanılacağını göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

Çıkışı `function3` aşağıdaki gibidir.

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

Aşağıdaki örnek, bir ters yineleme için negatif atlama değeri kullanmayı gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

Çıkışı `function4` aşağıdaki gibidir.

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Aralığın başlangıcı ve bitişi, aşağıdaki kodda olduğu gibi işlevler gibi ifadeler de olabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

Bu girişle çıkış `function5` aşağıdaki gibidir.

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

Sonraki örnekte, öğe döngüde gerekli olmadığında bir joker karakteri (\_) kullanımı gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

Çıktı aşağıdaki gibidir:

```
Number of elements in list1: 5
```

`Note`Dizi ifadelerinde ve `for...in` diğer hesaplama ifadelerinde kullanabilirsiniz, bu durumda `for...in` ifadenin özelleştirilmiş bir sürümü kullanılır. Daha fazla bilgi için bkz. [diziler](sequences.md), [zaman uyumsuz Iş akışları](asynchronous-workflows.md)ve [Hesaplama ifadeleri](computation-expressions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Lerin `for...to`İfadesini](loops-for-to-expression.md)
- [Lerin `while...do`İfadesini](loops-while-do-expression.md)
