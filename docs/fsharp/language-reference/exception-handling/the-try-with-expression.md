---
title: 'Özel durumlar: try...with İfadesi'
description: F# ' TRY... ' yı kullanmayı öğrenin ' i ' de, özel durum işleme için ifadesi.
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630251"
---
# <a name="exceptions-the-trywith-expression"></a>Özel durumlar: try...with İfadesi

Bu konuda, `try...with` F# dildeki özel durum işleme için kullanılan ifade olan ifade açıklanmaktadır.

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

İfade `try...with` , içindeki F#özel durumları işlemek için kullanılır. İçindeki `try...catch` C#ifadeye benzerdir. Önceki sözdiziminde, *İfade1* içindeki kod bir özel durum oluşturabilir. `try...with` İfade bir değer döndürür. Özel durum oluşturulursa, tüm ifade *İfade1*değerini döndürür. Bir özel durum oluşursa, her bir *Düzen* özel durumla karşılaştırılır ve ilk eşleşen düzen için, *özel durum işleyicisi*olarak bilinen karşılık gelen *ifade*, bu dal için yürütülür ve genel ifade Bu özel durum işleyicisindeki ifadenin değerini döndürür. Herhangi bir model eşleşmesi yoksa, özel durum, eşleşen bir işleyici bulunana kadar çağrı yığınını yayar. Özel durum işleyicilerindeki her bir ifadeden döndürülen değerlerin türleri, `try` bloktaki ifadeden döndürülen türle aynı olmalıdır.

Genellikle bir hata oluştuğu için, her bir özel durum işleyicisindeki ifadelerden döndürülebilecek geçerli bir değer olmadığı anlamına gelir. Sık kullanılan bir düzende, ifadenin türü bir seçenek türü olmalıdır. Aşağıdaki kod örneğinde bu desenler gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Özel durumlar .NET özel durumları olabilir veya F# özel durumlar olabilir. `exception` Anahtar sözcüğünü kullanarak F# özel durumlar tanımlayabilirsiniz.

Özel durum türü ve diğer koşulları filtrelemek için çeşitli desenler kullanabilirsiniz; Seçenekler aşağıdaki tabloda özetlenmiştir.

|Desen|Açıklama|
|-------|-----------|
|:? *özel durum türü*|Belirtilen .NET özel durum türüyle eşleşir.|
|:? *özel durum-* *tanımlayıcı* olarak tür|Belirtilen .NET özel durum türüyle eşleşir, ancak özel duruma adlandırılmış bir değer verir.|
|*özel durum-adı* (*bağımsız değişkenler*)|Bir F# özel durum türüyle eşleşir ve bağımsız değişkenleri bağlar.|
|*Tanımlayıcısını*|Herhangi bir özel durumla eşleşir ve adı özel durum nesnesine bağlar. **Eşdeğer:? System. Exception as**_Identifier_|
|*koşul* olduğunda *tanımlayıcı*|Koşul doğru ise herhangi bir özel durumla eşleşir.|

## <a name="examples"></a>Örnekler

Aşağıdaki kod örnekleri çeşitli özel durum işleyici desenlerinin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> Yapı, `try...finally` ifadeden ayrı bir ifadedir. `try...with` Bu nedenle, kodunuz hem `with` blok `finally` hem de blok gerektiriyorsa, iki ifadeyi iç içe geçirebilirsiniz.

> [!NOTE]
> Zaman uyumsuz iş `try...with` akışları ve diğer hesaplama ifadelerinde kullanabilirsiniz, bu durumda `try...with` ifadenin özelleştirilmiş bir sürümü kullanılır. Daha fazla bilgi için bkz. [zaman uyumsuz Iş akışları](../asynchronous-workflows.md)ve [Hesaplama ifadeleri](../computation-expressions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durum İşleme](index.md)
- [Özel Durum Türleri](exception-types.md)
- [Özel Durumlar: `try...finally` İfade](the-try-finally-expression.md)
