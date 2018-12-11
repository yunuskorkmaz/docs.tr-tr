---
title: 'Özel durumlar: Try... with ifadesi (F#)'
description: Nasıl kullanacağınızı öğrenin F# 'ile özel durum işleme için ifade try...'.
ms.date: 05/16/2016
ms.openlocfilehash: 946cf56f7abc4bd5e3a9f9acc52b868bd6c7f84a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127413"
---
# <a name="exceptions-the-trywith-expression"></a>Özel durumlar: Try... with ifadesi

Bu konu başlığı altında açıklanır `try...with` ifade, özel durum işleme için kullanılan ifade F# dili.

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

`try...with` Özel durumları işlemek için kullanılan ifade F#. Benzer `try...catch` C# deyimi. Önceki sözdiziminde, kodda *İfade1* bir özel durum oluşturabilir. `try...with` İfade bir değer döndürür. Hiçbir özel durum oluşturulursa, ifadenin değerini döndürür. *İfade1*. Bir özel durum oluşur, her *deseni* sırayla karşılık gelen ilk eşleşen deseni yanı sıra, özel durum ile karşılaştırıldığında *ifade*olarak bilinen *özel durum işleyicisi*, o dalı çalıştırılır ve genel ifade, özel durum işleyicisinde ifadenin değerini döndürür. Herhangi bir desen eşleşirse, eşleşen bir işleyici bulunana kadar özel durum çağrı yığınına yayar. Özel durum işleyicileri her ifadesinden döndürülen değerlerin türleri ifade öğesinden döndürülen tür eşleşmelidir `try` blok.

Sık sık hatayla ayrıca oluştu her özel durum işleyicisi ifadelerinde döndürüldüğü geçerli bir değer yoktur anlamına gelir. Bir seçenek türünde ifade türüne sahip sık kullanılan bir desendir. Aşağıdaki kod örneği, bu deseni gösterilmektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Özel durumlar, .NET özel durumları olabilir veya olabilir F# özel durumlar. Tanımlayabileceğiniz F# kullanarak özel durumları `exception` anahtar sözcüğü.

Özel durum türü ve diğer koşulları filtrelemek için desenler çeşitli kullanabilirsiniz; Seçenekler aşağıdaki tabloda özetlenmiştir.

|Desen|Açıklama|
|-------|-----------|
|:? *özel durum türü*|Belirtilen .NET özel durum türüyle eşleşen.|
|:? *özel durum türü* olarak *tanımlayıcısı*|Belirtilen .NET özel durum türüyle eşleşen, ancak özel durum adlandırılmış bir değer sağlar.|
|*özel durum adı*(*bağımsız değişkenleri*)|Eşleşen bir F# özel durum türünü ve bağımsız değişkenler bağlar.|
|*tanımlayıcı*|Herhangi bir özel durum ile eşleşen ve adı özel durum nesnesine bağlar. Eşdeğer **:? System.Exception olarak**_tanımlayıcısı_|
|*tanımlayıcı* olduğunda *koşulu*|Koşul true ise bir özel durumla eşleşir.|

## <a name="examples"></a>Örnekler

Aşağıdaki kod örnekleri, çeşitli özel durum işleyicisi desenlerinin kullanımını gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> `try...with` Yapıdır ayrı bir ifadeden `try...finally` ifade. Bu nedenle, kodunuzu hem gerektiriyorsa bir `with` blok ve `finally` bloğu iki ifadelerini iç içe gerekecektir.

> [!NOTE]
> Kullanabileceğiniz `try...with` içinde zaman uyumsuz iş akışları ve özelleştirilmiş sürümü durumda diğer hesaplama ifadeleri, hangi `try...with` ifade kullanılır. Daha fazla bilgi için [zaman uyumsuz iş akışları](../asynchronous-workflows.md), ve [hesaplama ifadeleri](../computation-expressions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel Durum Türleri](exception-types.md)
- [Özel durumlar: `try...finally` İfadesi](the-try-finally-expression.md)
