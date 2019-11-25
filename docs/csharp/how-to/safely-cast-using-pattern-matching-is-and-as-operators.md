---
title: Desenler ve as işleçlerini kullanarak güvenli bir şekilde atama
description: Değişkenleri farklı bir türe güvenle dönüştürmek için model eşleştirme tekniklerini kullanmayı öğrenin. Türleri güvenli bir şekilde dönüştürmek için model eşleştirmeyi ve as işleçlerini da kullanabilirsiniz.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 762f8135063f7256ce7a167c65013703d9249039
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973087"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Desenler ve as işleçlerini kullanarak güvenli bir şekilde atama

Nesneler çok biçimli olduğundan, bir taban sınıf türü değişkeni türetilmiş bir [türü](../programming-guide/types/index.md)tutmak mümkündür. Türetilmiş türün örnek üyelerine erişmek için değeri türetilmiş türe [dönüştürmek](../programming-guide/types/casting-and-type-conversions.md) gerekir. Ancak, bir atama <xref:System.InvalidCastException>oluşturma riskini oluşturur. C#yalnızca başarılı olacağı zaman bir tür dönüştürme gerçekleştiren [model eşleştirme](../pattern-matching.md) deyimleri sağlar. C#Ayrıca, bir değerin belirli bir türde olup olmadığını test etmek için [de ve işlecini](../language-reference/operators/type-testing-and-cast.md#is-operator) [de sağlar](../language-reference/operators/type-testing-and-cast.md#as-operator) .

Aşağıdaki kod, eşleşen `is` ifadesini gösterir. Bir yöntem bağımsız değişkenini test eden, olası bir türetilmiş tür kümesinden biri olup olmadığını belirlemede yöntemler içerir:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Önceki örnekte, model eşleştirme sözdiziminin birkaç özelliği gösterilmektedir. `if (a is Mammal m)` ve `if (o is Mammal m)` deyimleri, testi bir başlatma atamasıyla birleştirir. Atama yalnızca test başarılı olduğunda gerçekleşir. Değişken `m`, yalnızca atandığı katıştırılmış `if` deyimindeki kapsamdadır. `m` aynı yöntemde daha sonra erişemezsiniz. Etkileşimli pencerede deneyin.

Aşağıdaki örnek kodda gösterildiği gibi, [null yapılabilir bir değer türünün](../language-reference/builtin-types/nullable-value-types.md) bir değere sahip olup olmadığını test etmek için aynı sözdizimini de kullanabilirsiniz:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Önceki örnek, dönüşümlerle kullanılacak olan diğer model eşleme özelliklerini gösterir. `null` değeri için özel olarak denetleyerek null deseninin bir değişkenini test edebilirsiniz. Değişkenin çalışma zamanı değeri `null`olduğunda, bir türü denetleyen `is` bir bildirim her zaman `false`döndürür. `is` ifadesiyle eşleşen bir değer null değer `Nullable<int>``int?` türüne izin vermez, ancak başka bir değer türü için test edebilirsiniz. Yukarıdaki örnekteki `is` desenleri Nullable değer türleriyle sınırlı değildir. Bir başvuru türü değişkeninin bir `null`değere sahip olup olmadığını test etmek için bu desenleri de kullanabilirsiniz.

Yukarıdaki örnek ayrıca, değişkenin birçok farklı türden biri olabileceği bir `switch` deyiminde model eşleştirme `is` ifadesini nasıl kullanacağınızı gösterir.

Bir değişkenin verilen bir tür olup olmadığını test etmek istiyorsanız, ancak bunu yeni bir değişkene atamadıysanız, başvuru türleri ve null yapılabilir türler için `is` ve `as` işleçlerini kullanabilirsiniz. Aşağıdaki kod, bir değişken belirli bir türde ise test için, modelin bir parçası C# olan `is` ve `as` deyimlerinin nasıl kullanılacağını gösterir:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Bu kodu model eşleştirme koduyla karşılaştırarak görebileceğiniz gibi, model eşleştirme sözdizimi, testi ve atamayı tek bir bildirimde birleştirerek daha sağlam özellikler sağlar. Mümkün olan her seferinde model eşleştirme sözdizimini kullanın.

Bu örnekleri, [GitHub deponuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast)koda bakarak deneyebilirsiniz. Ya da örnekleri [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip)indirebilirsiniz.
