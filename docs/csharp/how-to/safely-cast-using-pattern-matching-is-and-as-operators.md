---
title: 'Nasıl yapılır: model eşleştirme ve ve olarak işleç kullanarak güvenli bir şekilde atama'
description: Değişkenleri farklı bir türe güvenle dönüştürmek için model eşleştirme tekniklerini kullanmayı öğrenin. Türleri güvenli bir şekilde dönüştürmek için model eşleştirmeyi ve as işleçlerini da kullanabilirsiniz.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 764a69869b8a5b8f76e2f58aced51761af73e50e
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566279"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Nasıl yapılır: model eşleştirme ve ve olarak işleç kullanarak güvenli bir şekilde atama

Nesneler çok biçimli olduğundan, bir taban sınıf türü değişkeni türetilmiş bir [türü](../programming-guide/types/index.md)tutmak mümkündür. Türetilmiş türün örnek üyelerine erişmek için değeri türetilmiş türe [dönüştürmek](../programming-guide/types/casting-and-type-conversions.md) gerekir. Ancak, bir atama bir oluşturma <xref:System.InvalidCastException>riskini oluşturur. C#yalnızca başarılı olacağı zaman bir tür dönüştürme gerçekleştiren [model eşleştirme](../pattern-matching.md) deyimleri sağlar. C#Ayrıca, bir [](../language-reference/operators/type-testing-and-cast.md#is-operator) değerin belirli [](../language-reference/operators/type-testing-and-cast.md#as-operator) bir türde olup olmadığını test etmek için de ve işlecini de sağlar.

Aşağıdaki kod, model eşleştirme `is` ifadesini gösterir. Bir yöntem bağımsız değişkenini test eden, olası bir türetilmiş tür kümesinden biri olup olmadığını belirlemede yöntemler içerir:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Önceki örnekte, model eşleştirme sözdiziminin birkaç özelliği gösterilmektedir. `if (a is Mammal m)` Ve`if (o is Mammal m)` deyimleri, testi bir başlatma ataması ile birleştirir. Atama yalnızca test başarılı olduğunda gerçekleşir. Değişken `m` , yalnızca atandığı katıştırılmış `if` ifadede kapsam içinde yer alabilir. Aynı yöntemde daha `m` sonra erişemezsiniz. Etkileşimli pencerede deneyin.

Aşağıdaki örnek kodda gösterildiği gibi, [null yapılabilir bir türün](../programming-guide/nullable-types/index.md) bir değere sahip olup olmadığını test etmek için aynı sözdizimini de kullanabilirsiniz:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Önceki örnek, dönüşümlerle kullanılacak olan diğer model eşleme özelliklerini gösterir. `null` Değeri özel olarak denetleyerek null deseninin bir değişkenini test edebilirsiniz. Değişkeninin `null`çalışma zamanı değeri olduğunda `is` , her zaman bir tür için denetim kümesi döndürülür `false`. Model eşleştirme `is` deyimleri, veya `Nullable<int>`gibi `int?` null yapılabilir değer türüne izin vermez, ancak diğer değer türleri için test edebilirsiniz.

Yukarıdaki örnek ayrıca, değişken birçok farklı türden biri olabilecek bir `is` `switch` deyimde model eşleştirme ifadesini nasıl kullanacağınızı gösterir.

Bir değişkenin verilen bir tür olup olmadığını test etmek istiyorsanız, ancak bunu yeni bir değişkene atamadıysanız, başvuru türleri ve null yapılabilir türler için `is` ve `as` işleçlerini kullanabilirsiniz. Aşağıdaki kod, bir değişken verilen bir türden `is` ise `as` test için, modelin bir parçası C# olan ve bir dilin parçası olan deyimlerinin nasıl kullanılacağını gösterir:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Bu kodu model eşleştirme koduyla karşılaştırarak görebileceğiniz gibi, model eşleştirme sözdizimi, testi ve atamayı tek bir bildirimde birleştirerek daha sağlam özellikler sağlar. Mümkün olan her seferinde model eşleştirme sözdizimini kullanın.

Bu örnekleri, [GitHub deponuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast)koda bakarak deneyebilirsiniz. Ya da örnekleri [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip)indirebilirsiniz.
