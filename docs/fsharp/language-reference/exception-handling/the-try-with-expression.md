---
title: 'Özel Durumlar: try...with İfadesi (F#)'
description: "Özel durum işleme için F # 'ile … Dene' ifadesi kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 588960c0f8ccedb431c37d0f1314bf1a293b638c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "44042172"
---
# <a name="exceptions-the-trywith-expression"></a>Özel Durumlar: try...with İfadesi

Bu konu başlığı altında açıklanır `try...with` ifade, özel durum F # dilinde işleme için kullanılan ifade.

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

`try...with` İfade, F # içinde özel durumları işlemek için kullanılır. Benzer `try...catch` C# deyimi. Önceki sözdiziminde, kodda *İfade1* bir özel durum oluşturabilir. `try...with` İfade bir değer döndürür. Hiçbir özel durum oluşturulursa, ifadenin değerini döndürür. *İfade1*. Bir özel durum oluşur, her *deseni* sırayla karşılık gelen ilk eşleşen deseni yanı sıra, özel durum ile karşılaştırıldığında *ifade*olarak bilinen *özel durum işleyicisi*, o dalı çalıştırılır ve genel ifade, özel durum işleyicisinde ifadenin değerini döndürür. Herhangi bir desen eşleşirse, eşleşen bir işleyici bulunana kadar özel durum çağrı yığınına yayar. Özel durum işleyicileri her ifadesinden döndürülen değerlerin türleri ifade öğesinden döndürülen tür eşleşmelidir `try` blok.

Sık sık hatayla ayrıca oluştu her özel durum işleyicisi ifadelerinde döndürüldüğü geçerli bir değer yoktur anlamına gelir. Bir seçenek türünde ifade türüne sahip sık kullanılan bir desendir. Aşağıdaki kod örneği, bu deseni gösterilmektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Özel durum .NET özel durumları olabilir veya F # özel durumlar olabilir. F # özel durumları kullanarak tanımlayabilirsiniz `exception` anahtar sözcüğü.

Özel durum türü ve diğer koşulları filtrelemek için desenler çeşitli kullanabilirsiniz; Seçenekler aşağıdaki tabloda özetlenmiştir.

|Desen|Açıklama|
|-------|-----------|
|:? *özel durum türü*|Belirtilen .NET özel durum türüyle eşleşen.|
|:? *özel durum türü* olarak *tanımlayıcısı*|Belirtilen .NET özel durum türüyle eşleşen, ancak özel durum adlandırılmış bir değer sağlar.|
|*özel durum adı*(*bağımsız değişkenleri*)|Bir F # özel durum türüyle eşleşen ve bağımsız değişkenler bağlar.|
|*tanımlayıcı*|Herhangi bir özel durum ile eşleşen ve adı özel durum nesnesine bağlar. Eşdeğer **:? System.Exception olarak *** tanımlayıcısı*|
|*tanımlayıcı* olduğunda *koşulu*|Koşul true ise bir özel durumla eşleşir.|

## <a name="examples"></a>Örnekler

Aşağıdaki kod örnekleri, çeşitli özel durum işleyicisi desenlerinin kullanımını gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

>[!NOTE]
`try...with` Yapıdır ayrı bir ifadeden `try...finally` ifade. Bu nedenle, kodunuzu hem gerektiriyorsa bir `with` blok ve `finally` bloğu iki ifadelerini iç içe gerekecektir.

>[!NOTE]
Kullanabileceğiniz `try...with` içinde zaman uyumsuz iş akışları ve özelleştirilmiş sürümü durumda diğer hesaplama ifadeleri, hangi `try...with` ifade kullanılır. Daha fazla bilgi için [zaman uyumsuz iş akışları](../asynchronous-workflows.md), ve [hesaplama ifadeleri](../computation-expressions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel Durum Türleri](exception-types.md)
- [Özel durumlar: `try...finally` ifadesi](the-try-finally-expression.md)
