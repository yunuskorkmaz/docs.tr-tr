---
title: 'Nasıl yapılır: desen eşleştirme kullanarak güvenli bir şekilde noktaya yayın ve olduğu ve işleçler'
description: Teknikleri desen değişkenleri farklı bir türe güvenli bir şekilde kullanmayı öğrenin. Desen eşleştirme kullan yanı sıra olduğunu ve güvenli bir şekilde dönüştürmek için işleçleri türleri.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 6887f6977511224a2a5c867e69df306e3bc2cc25
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169872"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Nasıl yapılır: desen eşleştirme kullanarak güvenli bir şekilde noktaya yayın ve olduğu ve işleçler

Nesneler çok biçimli olduğundan türetilmiş tutmak için bir temel sınıf türünde bir değişken için olası [türü](../programming-guide/types/index.md). Türetilen türün örnek üyeleri erişmek için gerekli olduğu [atama](../programming-guide/types/casting-and-type-conversions.md) geri türetilmiş bir tür için değer. Ancak, bir yayın atma riskini oluşturur bir <xref:System.InvalidCastException>. C# sağlar [desen eşleştirme](../pattern-matching.md) yalnızca başarılı olur, koşullu olarak bir dönüştürme gerçekleştirmek deyimleri. C# ayrıca sağlar [olduğu](../language-reference/keywords/is.md) ve [olarak](../language-reference/keywords/as.md) belirli türde bir değer olup olmadığını sınayacak işleçleri.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki kod, eşleşen deseni gösterir `is` deyimi. Olası bir türetilmiş türleri kümesinin olup olmadığının yöntemi bağımsız değişken test yöntemleri içerir:

[!code-csharp-interactive[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Önceki örnekte, birkaç desen eşleştirme sözdizimi özelliklerini gösterir. `if (a is Mammal m)` Ve `if (o is Mammal m)` deyimleri test başlatma atama ile birleştirin. Atama, yalnızca testin ne zaman başarılı gerçekleşir. Değişken `m` yalnızca katıştırılmış kapsam içinde `if` burada atanmış deyimi. Erişemiyorsanız `m` aynı yöntemi daha sonra. Etkileşimli pencerede deneyin.

Test etmek için de aynı sözdizimini kullanabilirsiniz bir [boş değer atanabilir tür](../programming-guide/nullable-types/index.md) aşağıdaki örnek kodda gösterildiği gibi bir değer vardır:

[!code-csharp-interactive[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Önceki örnekte dönüştürmeler kullanmak için desen eşleştirme, diğer özelliklerini gösterir. Null desen için bir değişken için özel olarak işaretleyerek test edebilirsiniz `null` değeri. Değişkeninin çalışma zamanı değeri olduğunda `null`e `is` her zaman bir tür döndüren için deyimi denetimi `false`. Desen eşleştirme `is` deyimi değil izin bir boş değer atanabilir değer türü gibi `int?` veya `Nullable<int>`, ancak herhangi bir değer türü için test edebilirsiniz.

Desen eşleştirme kullanma önceki örnek ayrıca gösterir `is` ifadesinde bir `switch` burada değişkeni olabilir birçok farklı türde bir ifade.

Verilen tür değişken ise, test, ancak yeni bir değişkene atayın değil istiyorsanız kullanabileceğiniz `is` ve `as` işleçler başvuru türleri ve boş değer atanabilir türler için. Aşağıdaki kod nasıl kullanılacağını gösterir `is` ve `as` belirtilen türde bir değişken olup olmadığını test etmek için desen eşleştirme sunulmadan önce C# dilinin bir parçası olan deyimleri:

[!code-csharp-interactive[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Desen eşleştirme sözdizimi desen eşleştirme kodu şu kodla karşılaştırarak görebileceğiniz gibi test ve tek bir deyimde atama birleştirerek daha güçlü özellikler sağlar. Desen eşleştirme sözdizimi mümkün olduğunca kullanın.

Bu örnekler kodda bakarak deneyebilirsiniz bizim [GitHub deposu](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
