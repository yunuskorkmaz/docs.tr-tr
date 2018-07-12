---
title: 'Özel Durumlar: try...with İfadesi (F#)'
description: "Özel durum işleme için F # 'ile... deneyin' ifadesi kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 5e6e16d5fba88841d567512ba7e08a2e8d17bdba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565294"
---
# <a name="exceptions-the-trywith-expression"></a>Özel Durumlar: try...with İfadesi

Bu konuda açıklanmaktadır `try...with` ifade, özel durum işleme F # dili için kullanılan ifade.


## <a name="syntax"></a>Sözdizimi

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>Açıklamalar
`try...with` İfade F # özel durumları işlemek için kullanılır. Aşağıdakine benzer `try...catch` C# deyimi. Önceki sözdiziminde, kodda *İfade1* bir özel durum oluşturabilir. `try...with` İfade bir değer döndürür. Hiçbir özel durum, tüm ifadenin değerini döndürür. *İfade1*. Bir özel durum oluşur, her *düzeni* özel ve karşılık gelen ilk eşleştirme deseni için sırayla karşılaştırılır *ifade*, olarak bilinen *özel durum işleyici*, o şubedeki yürütülür ve genel ifade bu özel durum işleyici ifadesinin değerini döndürür. Hiçbir desen eşleşirse, eşleşen bir işleyici bulunana kadar özel durum çağrı yığınına yayar. Özel durum işleyicileri her ifadesinden döndürdüğü değer türü ifadesinde döndürülen türüyle eşleşmelidir `try` bloğu.

Sık sık hatayla de oluştuğunu olgu her özel durum işleyici ifadelerinde öğesinden döndürülen geçerli bir değer olduğu anlamına gelir. Sık kullanılan bir desen bir seçenek türü ifadesinin olmalıdır. Aşağıdaki kod örneği, bu deseni gösterilmektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Özel durumlar, .NET özel durumları veya F # özel durumlar olabilir. Kullanarak F # özel durumlar tanımlayabilirsiniz `exception` anahtar sözcüğü.

Özel durum türü ve diğer koşulları filtrelemek için desenleri çeşitli kullanabilirsiniz; seçenekleri aşağıdaki tabloda özetlenmiştir.


|Desen|Açıklama|
|-------|-----------|
|:? *özel durum türü*|Belirtilen .NET özel durum türü eşleşir.|
|:? *özel durum türü* olarak *tanımlayıcısı*|Belirtilen .NET özel durum türü eşleşir, ancak özel bir adlandırılmış değeri verir.|
|*özel durum adı*(*bağımsız değişkenleri*)|F # özel durum türü ile eşleşen ve bağımsız değişkenler bağlar.|
|*Tanımlayıcı*|Herhangi bir özel durum ile eşleşen ve özel durum nesnesi adı bağlar. Eşdeğer **:? System.Exception olarak *** tanımlayıcısı*|
|*tanımlayıcı* zaman *koşulu*|Koşul doğru ise, bir özel durumla eşleşir.|

## <a name="examples"></a>Örnekler
Aşağıdaki kod örneğinde çeşitli özel durum işleyici desenlerini kullanımını gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]
    
>[!NOTE] 
`try...with` Yapıdır ayrı ifadesinden `try...finally` ifade. Bu nedenle, kodunuzun her ikisi de gerektiriyorsa bir `with` bloğu ve `finally` bloğu, iki ifadeleri iç içe gerekecektir.

>[!NOTE] 
Kullanabileceğiniz `try...with` içinde zaman uyumsuz iş akışları ve özelleştirilmiş bir sürümünü durumda diğer hesaplama ifadeleri, hangi `try...with` ifade kullanılır. Daha fazla bilgi için bkz: [zaman uyumsuz iş akışları](../asynchronous-workflows.md), ve [hesaplama ifadeleri](../computation-expressions.md).


## <a name="see-also"></a>Ayrıca Bkz.
[Özel Durum İşleme](index.md)

[Özel Durum Türleri](exception-types.md)

[Özel durumlar: `try...finally` ifade](the-try-finally-expression.md)
