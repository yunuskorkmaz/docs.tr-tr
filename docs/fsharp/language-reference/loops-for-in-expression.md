---
title: 'Döngüler: for...in İfadesi (F#)'
description: 'Bkz. nasıl F # for... ifadesinde yapı döngü numaralandırılabilir bir koleksiyon içindeki bir desenle eşleşen üzerinden yinelemek için kullanılır.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: eaf0f4fc6419d8e0bff46795120ee5e42c4efe1d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="loops-forin-expression"></a>Döngüler: for...in İfadesi

Bu döngü yapısı aralık ifade, sırası, liste, dizi veya numaralandırma destekleyen diğer yapı gibi numaralandırılabilir bir koleksiyon içindeki bir desenle eşleşen üzerinden yinelemek için kullanılır.


## <a name="syntax"></a>Sözdizimi

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Açıklamalar
`for...in` İfade için karşılaştırılabilir `for each` diğer .NET dilleri deyiminde numaralandırılabilir koleksiyonundaki değerleri üzerinde döngü için kullanıldığından. Ancak, `for...in` desen eşleştirme içinde tüm koleksiyon yerine yalnızca yineleme koleksiyon üzerinden de destekler.

Numaralandırılabilir ifade numaralandırılabilir bir koleksiyon olarak veya kullanarak belirtilen `..` olarak bir tamsayı türünde bir aralık işleci. Numaralandırılabilir koleksiyonları listeler, dizileri, dizileri, kümeleri, eşlemeleri vb. içerir. Uygulayan herhangi bir türü `System.Collections.IEnumerable` kullanılabilir.

Ne zaman, hızlı bir aralık kullanarak `..` işleci, aşağıdaki söz dizimini kullanabilirsiniz.

*Başlat* ... *Son*

Adlı bir artış içeren bir sürümünü de kullanabilirsiniz *atla*, aşağıdaki kod gibi.

*Başlat* ... *atla* ... *Son*

Tam sayı aralıkları ve basit bir sayaç değişken kalıp olarak kullandığınızda, tipik davranışı her bir yineleme 1 sayaç değişkeni artırılacak olmakla birlikte, aralık bir atlama değeri içeriyorsa, bu sayaç tarafından atlama değeri yerine artırılır.

Düzende eşleşen değerleri de gövde ifadesinde kullanılabilir.

Aşağıdaki kod örnekleri kullanımını göstermek `for...in` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

Çıktı aşağıdaki gibidir:

```
1
5
100
450
788
```

Aşağıdaki örnekte nasıl sırası döngü ve yerine basit bir değişkene bir demet deseni kullanmayı gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

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

Aşağıdaki örnek, bir basit tamsayı aralığında döngü gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Function1 çıktı aşağıdaki gibidir.

```
1 2 3 4 5 6 7 8 9 10
```

Aşağıdaki örnek, bir aralığı her bir öğe içeren bir Atla 2 ' olan bir aralığı üzerinden döngü gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

Çıktısını `function2` aşağıdaki gibidir.

```
1 3 5 7 9
```

Aşağıdaki örnek, bir karakter aralığı kullanmayı gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

Çıktısını `function3` aşağıdaki gibidir.

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

Aşağıdaki örnek, geriye doğru yineleme için negatif atlama değeri kullanmayı gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

Çıktısını `function4` aşağıdaki gibidir.

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Başlangıç ve bitiş aralığının İşlevler, aşağıdaki kod olduğu gibi ifadeler de olabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

Çıktısını `function5` bu girişle aşağıdaki gibidir.

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

Öğe bir döngüde gerekli olmadığında sonraki örnek bir joker karakteri (_) kullanımını göstermektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

Çıktı aşağıdaki gibidir:

```
Number of elements in list1: 5
```

`Note` Kullanabileceğiniz `for...in` sequence ifadeleri ve diğer hesaplama ifadeleri özelleştirilmiş bir sürümünü durumda içinde `for...in` ifade kullanılır. Daha fazla bilgi için bkz: [sıraları](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [hesaplama ifadeleri](computation-expressions.md).


## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Döngüler: `for...to` ifade](loops-for-to-expression.md)

[Döngüler: `while...do` ifade](loops-while-do-expression.md)
