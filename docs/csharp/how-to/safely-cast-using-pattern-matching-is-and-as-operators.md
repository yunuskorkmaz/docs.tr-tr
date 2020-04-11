---
title: Desen eşleştirme ve is ve operatörler olarak kullanarak güvenli bir şekilde döküm nasıl
description: Değişkenleri güvenli bir şekilde farklı bir türe atmak için desen eşleştirme tekniklerini kullanmayı öğrenin. Türleri güvenli bir şekilde dönüştürmek için desen eşleştirme yanı sıra ve operatörler olarak kullanabilirsiniz.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 60e69a8ef55484e3b04f1674c35a1c5dadfa3b7c
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121004"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Desen eşleştirme ve is ve operatörler olarak kullanarak güvenli bir şekilde döküm nasıl

Nesneler çok morfik olduğundan, taban sınıf [türünden](../programming-guide/types/index.md)bir değişkenin türetilmiş bir türü tutması mümkündür. Türetilen türün örnek üyelerine erişmek için, değeri türetilmiş türe geri [atmak](../programming-guide/types/casting-and-type-conversions.md) gerekir. Ancak, bir döküm atma <xref:System.InvalidCastException>riski oluşturur. C# yalnızca başarılı olduğunda koşullu olarak bir döküm gerçekleştiren [desen eşleştirme](../pattern-matching.md) deyimleri sağlar. C# ayrıca [bir](../language-reference/operators/type-testing-and-cast.md#is-operator) değerin belirli bir türde olup olmadığını test etmek için is ve [operatörler olarak](../language-reference/operators/type-testing-and-cast.md#as-operator) sağlar.

Aşağıdaki örnek, desen eşleştirme `is` deyiminin nasıl kullanılacağını gösterir:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Önceki örnek, desen eşleşen sözdizimi birkaç özelliklerini gösterir. Deyim, `if (a is Mammal m)` testi bir başlatma atamasıyla birleştirir. Atama yalnızca test başarılı olduğunda oluşur. Değişken `m` yalnızca atandığı katıştırılmış `if` deyimin kapsamıdır. Daha sonra `m` aynı yöntemle erişemezsiniz. Önceki örnek, bir nesneyi belirli bir türe dönüştürmek için [ `as` işlecinin](../language-reference/operators/type-testing-and-cast.md#as-operator) nasıl kullanılacağını da gösterir.

Aşağıdaki örnekte gösterildiği [gibi, nullable değer türü](../language-reference/builtin-types/nullable-value-types.md) bir değer varsa, sınama için aynı sözdizimini de kullanabilirsiniz:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Önceki örnek, dönüşümlerle kullanmak üzere eşleşen desen diğer özelliklerini gösterir. `null` Değeri özel olarak denetleyerek null deseni için bir değişkeni sınayabilirsiniz. Değişkenin çalışma zamanı değeri `null`olduğunda, `is` bir tür için `false`bir deyim her zaman döndürür. Desen eşleştirme `is` deyimi gibi boşatılabilir bir değer `int?` türüne izin `Nullable<int>`vermez, ancak başka bir değer türü için sınama yapabilirsiniz. Önceki `is` örnekteki desenler nullable değer türleri ile sınırlı değildir. Ayrıca, başvuru türünden bir değişkenin bir değeri olup olmadığını veya `null`.

Önceki örnek, değişkenin birçok farklı türden `switch` biri olabileceği bir deyimdeki tür deseni nasıl kullandığınızı da gösterir.

Bir değişkenin belirli bir tür olup olmadığını sınamak, ancak yeni bir değişkene `is` `as` atamamak istiyorsanız, başvuru türleri ve nullable değer türleri için ve işleçleri kullanabilirsiniz. Aşağıdaki kod, bir `is` değişkenin `as` belirli bir türde olup olmadığını sınamak için desen eşleştirmesi kullanılmadan önce C# dilinin bir parçası olan ifadelerin nasıl kullanılacağını gösterir:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Bu kodu desen eşleştirme koduyla karşılaştırarak görebileceğiniz gibi, desen eşleştirme sözdizimi, testi ve atamayı tek bir deyimde birleştirerek daha sağlam özellikler sağlar. Deseni eşleştirme sözdizimini mümkün olduğunca kullanın.

Bu örnekleri [GitHub depomuzdaki](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/safelycast)koda bakarak deneyebilirsiniz. Veya bir zip [dosyası olarak](../../../samples/snippets/csharp/how-to/safelycast.zip)örnekleri indirebilirsiniz.
