---
title: 'Döngüler: for...in İfadesi (F#)'
description: 'Bkz. nasıl F # for... ifadesinde döngü yapısı bir sıralanabilir koleksiyonun içindeki bir desenle eşleşmeleri üzerinden yinelemek için kullanılır.'
ms.date: 05/16/2016
ms.openlocfilehash: c4fba1f1dea3993cafa2e37ad0f32d9fb2eed85a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46287877"
---
# <a name="loops-forin-expression"></a>Döngüler: for...in İfadesi

Bu uvozuje konstruktor aralık ifadesi, sıra, liste, dizi veya numaralandırma destekleyen diğer yapı gibi bir sıralanabilir koleksiyonun içindeki bir desenle eşleşmeleri üzerinden yinelemek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Açıklamalar

`for...in` İfade için karşılaştırılabilir `for each` diğer .NET dilleri deyiminde bir sıralanabilir koleksiyonun değerleri üzerinde döngü için kullanıldığından. Ancak, `for...in` koleksiyon yerine yalnızca yineleme üzerinden tüm koleksiyon üzerinde desen de destekler.

Numaralandırılabilir ifade bir sıralanabilir koleksiyonun olarak veya kullanılarak belirtilebilir `..` olarak bir tamsayı türü üzerinde bir aralık işleci. Numaralandırılabilir koleksiyonları listeler, dizileri, diziler, kümeleri, haritalar ve benzeri içerir. Uygulayan herhangi bir tür `System.Collections.IEnumerable` kullanılabilir.

Ne zaman, express aralığı kullanarak `..` işleci, aşağıdaki söz dizimini kullanabilirsiniz.

*Başlangıç* ... *Son*

Adlı bir artışı içeren bir sürümünü de kullanabilirsiniz *atla*, aşağıdaki kodda gibi.

*Başlangıç* ... *atla* ... *Son*

İntegral aralığı ve basit bir sayaç değişkeni bir desen kullandığınızda, her yinelemede 1 sayaç değişkeni artırılacak normal davranış olduğu halde aralık bir atlama değeri içeriyorsa, bu sayaç tarafından atlama değeri bunun yerine artırılır.

Düzende eşleşen değerleri de gövdesi ifadesinde kullanılabilir.

Aşağıdaki kod örnekleri kullanımını gösteren `for...in` ifade.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

Çıktı aşağıdaki gibidir:

```
1
5
100
450
788
```

Aşağıdaki örnek nasıl bir dizisi üzerinde döngü gerçekleştirmek ve yerine basit bir değişken olarak bir tanımlama grubu düzeni kullanmayı gösterir.

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

İşlev1 çıktısı aşağıdaki gibidir.

```
1 2 3 4 5 6 7 8 9 10
```

Aşağıdaki örnek, her bir öğe aralığı içeren bir atlama 2 ' nin bir aralık boyunca döngüye gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

Çıkışı `function2` gibidir.

```
1 3 5 7 9
```

Aşağıdaki örnek, bir karakter aralığı kullanma işlemini gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

Çıkışı `function3` gibidir.

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

Aşağıdaki örnek, bir geriye doğru yineleme için negatif atlama değeri kullanmayı gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

Çıkışı `function4` gibidir.

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Başlangıç ve bitiş aralığı gibi işlevler, aşağıdaki kodda gösterildiği gibi ifadeler de olabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

Çıkışı `function5` bu girişle aşağıdaki gibidir.

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

Sonraki örnek, bir joker karakter kullanımını gösterir (\_) ne zaman öğesi gerekli değildir döngüde.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

Çıktı aşağıdaki gibidir:

```
Number of elements in list1: 5
```

`Note` Kullanabileceğiniz `for...in` sequence ifadeleri ve diğer hesaplama ifadeleri, özelleştirilmiş bir sürümünü durumda `for...in` ifade kullanılır. Daha fazla bilgi için [dizileri](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [hesaplama ifadeleri](computation-expressions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Döngüler: `for...to` ifadesi](loops-for-to-expression.md)
- [Döngüler: `while...do` ifadesi](loops-while-do-expression.md)
