---
title: Sorgu ifadelerindeki özel durumları işleme (C#'da LINQ)
description: C#'daki LINQ sorgu ifadelerindeki özel durumları nasıl işleyeceğinizi öğrenin.
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688507"
---
# <a name="handle-exceptions-in-query-expressions"></a>Sorgu ifadelerinde özel durumları işleme

Sorgu ifadesi bağlamında herhangi bir yöntemi çağırmak mümkündür. Ancak, sorgu ifadesinde veri kaynağının içeriğini değiştirme veya özel durum atma gibi bir yan etki oluşturabilecek herhangi bir yöntemi çağırmaktan kaçınmanızı öneririz. Bu örnek, özel durum işleme genel .NET yönergelerini ihlal etmeden bir sorgu ifadesinde yöntemleri çağırdığınızda özel durumlar alabilmeyi nasıl önleyisiniz gösterir. Bu yönergeler, belirli bir içeriğe neden atıldığını anladığınızda belirli bir özel durumu yakalamanın kabul edilebilir olduğunu belirtir. Daha fazla bilgi [için Özel Durumlar için En İyi Uygulamalar'a](../../standard/exceptions/best-practices-for-exceptions.md)bakın.

Son örnek, sorgunun yürütülmesi sırasında bir özel durum atmanız gerektiğinde bu servis taleplerini nasıl işleyeceğinizgöster.

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel durum işleme kodunun sorgu ifadesinin dışına nasıl taşınılacağını gösterir. Bu, yalnızca yöntem sorgunun yerel değişkenlerine bağlı olmadığında mümkündür.

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a>Örnek

Bazı durumlarda, sorgu nun içinden atılan bir özel durum için en iyi yanıt, sorgu yürütmesini hemen durdurmak olabilir. Aşağıdaki örnek, sorgu gövdesinin içinden atılabilecek özel durumların nasıl işleyeceğini gösterir. Sorgu `SomeMethodThatMightThrow` yürütmesinin durmasını gerektiren bir özel durum neden olabileceğini varsayalım.

Bloğun sorgunun `try` kendisini değil, döngüyü `foreach` kapladığını unutmayın. Bunun nedeni, `foreach` döngünün sorgunun gerçekte yürütüldolduğu nokta olmasıdır. Daha fazla bilgi için [LINQ sorgularına giriş etüt ünt.'e](../programming-guide/concepts/linq/introduction-to-linq-queries.md)bakın.

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
