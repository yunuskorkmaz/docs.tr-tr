---
title: 'Nasıl yapılır: model eşleştirme ve ve olarak işleç kullanarak güvenli bir şekilde atama'
description: Değişkenleri farklı bir türe güvenle dönüştürmek için model eşleştirme tekniklerini kullanmayı öğrenin. Türleri güvenli bir şekilde dönüştürmek için model eşleştirmeyi ve as işleçlerini da kullanabilirsiniz.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: d82c60374db637bb8ac879a23e2d74c39194ca18
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353729"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Nasıl yapılır: model eşleştirme ve ve olarak işleç kullanarak güvenli bir şekilde atama

Nesneler çok biçimli olduğundan, bir taban sınıf türü değişkeni türetilmiş bir [türü](../programming-guide/types/index.md)tutmak mümkündür. Türetilmiş türün örnek üyelerine erişmek için değeri türetilmiş türe [dönüştürmek](../programming-guide/types/casting-and-type-conversions.md) gerekir. Ancak, bir atama @no__t oluşturma riskini oluşturur-0. C#yalnızca başarılı olacağı zaman bir tür dönüştürme gerçekleştiren [model eşleştirme](../pattern-matching.md) deyimleri sağlar. C#Ayrıca, bir değerin belirli bir türde olup olmadığını test etmek için [de ve işlecini](../language-reference/operators/type-testing-and-cast.md#is-operator) [de sağlar](../language-reference/operators/type-testing-and-cast.md#as-operator) .

Aşağıdaki kod, eşleşen `is` ifadesini gösterir. Bir yöntem bağımsız değişkenini test eden, olası bir türetilmiş tür kümesinden biri olup olmadığını belirlemede yöntemler içerir:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Önceki örnekte, model eşleştirme sözdiziminin birkaç özelliği gösterilmektedir. @No__t-0 ve `if (o is Mammal m)` deyimleri, testi bir başlatma atamasıyla birleştirir. Atama yalnızca test başarılı olduğunda gerçekleşir. @No__t-0 değişkeni yalnızca atandığı katıştırılmış `if` deyimindeki kapsam içinde. @No__t-0 ' dan daha sonra aynı yöntemde erişemezsiniz. Etkileşimli pencerede deneyin.

Aşağıdaki örnek kodda gösterildiği gibi, [null yapılabilir bir değer türünün](../programming-guide/nullable-types/index.md) bir değere sahip olup olmadığını test etmek için aynı sözdizimini de kullanabilirsiniz:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Önceki örnek, dönüşümlerle kullanılacak olan diğer model eşleme özelliklerini gösterir. @No__t-0 değeri için özel olarak denetleyerek null deseninin bir değişkenini test edebilirsiniz. Değişkenin çalışma zamanı değeri `null` olduğunda, bir tür için bir `is` bildirim denetimi her zaman `false` ' i döndürür. @No__t-0 ifadesiyle eşleşen desenler, `int?` veya `Nullable<int>` gibi null olabilen değer türüne izin vermez, ancak başka bir değer türü için test edebilirsiniz. Yukarıdaki örnekteki `is` desenleri null yapılabilir değer türleriyle sınırlı değildir. Ayrıca, bir başvuru türü değişkeninin bir değere sahip olup olmadığını test etmek için bu desenleri kullanabilirsiniz `null`.

Yukarıdaki örnek ayrıca, değişkenin birçok farklı türden biri olabileceği bir `switch` deyiminde eşleşen `is` ifadesini nasıl kullanacağınızı gösterir.

Bir değişkenin verilen bir tür olup olmadığını test etmek istiyorsanız, ancak bunu yeni bir değişkene atamadıysanız, `is` ve `as` işleçlerini başvuru türleri ve null yapılabilir türler için kullanabilirsiniz. Aşağıdaki kod, bir değişken verilen bir türden ise test için, modelin bir parçası C# olan `is` ve `as` deyimlerinin nasıl kullanılacağını gösterir:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Bu kodu model eşleştirme koduyla karşılaştırarak görebileceğiniz gibi, model eşleştirme sözdizimi, testi ve atamayı tek bir bildirimde birleştirerek daha sağlam özellikler sağlar. Mümkün olan her seferinde model eşleştirme sözdizimini kullanın.

Bu örnekleri, [GitHub deponuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast)koda bakarak deneyebilirsiniz. Ya da örnekleri [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip)indirebilirsiniz.
