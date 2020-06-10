---
title: Desenler ve as işleçlerini kullanarak güvenli bir şekilde atama
description: Değişkenleri farklı bir türe güvenle dönüştürmek için model eşleştirme tekniklerini kullanmayı öğrenin. Türleri güvenli bir şekilde dönüştürmek için model eşleştirmeyi ve as işleçlerini da kullanabilirsiniz.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: f10ce837057cc61b84130f237a13af708849dfc5
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662972"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Desenler ve as işleçlerini kullanarak güvenli bir şekilde atama

Nesneler çok biçimli olduğundan, bir taban sınıf türü değişkeni türetilmiş bir [türü](../programming-guide/types/index.md)tutmak mümkündür. Türetilmiş türün örnek üyelerine erişmek için değeri türetilmiş türe [dönüştürmek](../programming-guide/types/casting-and-type-conversions.md) gerekir. Ancak, bir atama bir oluşturma riskini oluşturur <xref:System.InvalidCastException> . C#, yalnızca başarılı olacağı zaman bir tür dönüştürme gerçekleştiren [desenler ile eşleşen](../pattern-matching.md) deyimler sağlar. C# Ayrıca, bir değerin belirli bir türde olup olmadığını test etmek için [,](../language-reference/operators/type-testing-and-cast.md#is-operator) [ve işlecini de](../language-reference/operators/type-testing-and-cast.md#as-operator) sağlar.

Aşağıdaki örnek, model eşleştirme ifadesinin nasıl kullanılacağını gösterir `is` :

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs" id="PatternMatchingIs":::

Önceki örnekte, model eşleştirme sözdiziminin birkaç özelliği gösterilmektedir. `if (a is Mammal m)`İfade, testi bir başlatma ataması ile birleştirir. Atama yalnızca test başarılı olduğunda gerçekleşir. Değişken, `m` yalnızca atandığı katıştırılmış ifadede kapsam içinde yer `if` alabilir. `m`Aynı yöntemde daha sonra erişemezsiniz. Yukarıdaki örnek ayrıca, bir nesneyi belirtilen bir türe dönüştürmek için [ `as` işlecinin](../language-reference/operators/type-testing-and-cast.md#as-operator) nasıl kullanılacağını gösterir.

Aşağıdaki örnekte gösterildiği gibi, [null yapılabilir bir değer türünün](../language-reference/builtin-types/nullable-value-types.md) bir değere sahip olup olmadığını test etmek için aynı sözdizimini de kullanabilirsiniz:

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs" id="PatternMatchingNullable":::

Önceki örnek, dönüşümlerle kullanılacak olan diğer model eşleme özelliklerini gösterir. Değeri özel olarak denetleyerek null deseninin bir değişkenini test edebilirsiniz `null` . Değişkeninin çalışma zamanı değeri olduğunda `null` , `is` her zaman bir tür için denetim kümesi döndürülür `false` . Model eşleştirme `is` deyimleri, veya gibi null yapılabilir değer türüne izin vermez `int?` `Nullable<int>` , ancak diğer değer türleri için test edebilirsiniz. `is`Yukarıdaki örnekteki desenler Nullable değer türleriyle sınırlı değildir. Bu desenleri, bir başvuru türü değişkeninin bir değere sahip olup olmadığını test etmek için de kullanabilirsiniz `null` .

Yukarıdaki örnek ayrıca, `switch` değişkenin birçok farklı türden biri olabileceği bir ifadede tür deseninin nasıl kullanıldığını gösterir.

Bir değişkenin verilen bir tür olup olmadığını test etmek istiyorsanız, ancak bunu yeni bir değişkene atamadıysanız, `is` `as` başvuru türleri ve null yapılabilir değer türleri için ve işleçlerini kullanabilirsiniz. Aşağıdaki kod, `is` `as` bir değişken belirli bir türde ise test 'e, model dilinin bir parçası olan ve deyimlerinin nasıl kullanıldığını gösterir:

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs" id="IsAndAs":::

Bu kodu model eşleştirme koduyla karşılaştırarak görebileceğiniz gibi, model eşleştirme sözdizimi, testi ve atamayı tek bir bildirimde birleştirerek daha sağlam özellikler sağlar. Mümkün olan her seferinde model eşleştirme sözdizimini kullanın.
