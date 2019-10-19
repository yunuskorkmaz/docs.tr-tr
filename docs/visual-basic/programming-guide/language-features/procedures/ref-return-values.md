---
title: Ref dönüş değerleri (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: 7401fdd0fa876d21a87dbe9faf9d979e6b3bdc5c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581130"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Başvuru dönüş değerleri için destek (Visual Basic)

7,0 ile C# başlayarak, C# dil *Başvuru dönüş değerlerini*destekler. Başvuru dönüş değerlerini anlamanın bir yolu, bir yönteme başvuruya göre geçirilen bağımsız değişkenlerin tersidir. Başvuruya göre geçirilen bir bağımsız değişken değiştirildiğinde, değişiklikler çağıranın değişkeninin değerine yansıtılır. Bir yöntem bir çağırana bir başvuru dönüş değeri sağlıyorsa, çağıran tarafından başvuru dönüş değeri yapılan değişiklikler çağrılan metodun verilerinde yansıtılır.

Visual Basic, başvuru dönüş değerleri olan Yöntemler yazmanıza izin vermez, ancak başvuru dönüş değerlerini kullanmanıza izin verir. Diğer bir deyişle, başvuru dönüş değeri olan bir yöntemi çağırabilir ve bu dönüş değerini değiştirebilir ve başvuru dönüş değerindeki değişiklikler çağrılan metodun verilerinde yansıtılır.

## <a name="modifying-the-ref-return-value-directly"></a>Başvuru dönüş değerini doğrudan değiştirme

Her zaman başarılı ve `ByRef` parametreye sahip olmayan yöntemler için başvuru dönüş değerini doğrudan değiştirebilirsiniz. Bunu, başvuru dönüş değeri döndüren deyimlere yeni değeri atayarak yapabilirsiniz.

Aşağıdaki C# örnek, bir iç değeri artıran ve başvuru dönüş değeri olarak döndüren bir `NumericValue.IncrementValue` yöntemi tanımlar.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Başvuru dönüş değeri daha sonra aşağıdaki Visual Basic örneğinde çağıran tarafından değiştirilir. @No__t_0 yöntemi çağrısının bulunduğu satırın yöntemine bir değer atamayacağını unutmayın. Bunun yerine, yöntemi tarafından döndürülen başvuru dönüş değerine bir değer atar.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Yardımcı yöntemi kullanma

Diğer durumlarda, doğrudan yöntem çağrısının başvuru dönüş değerini değiştirmek her zaman istenmeyebilir. Örneğin, bir dize döndüren arama yöntemi her zaman bir eşleşme bulmayabilir. Bu durumda, başvuru dönüş değerini yalnızca arama başarılı olursa değiştirmek istersiniz.

Aşağıdaki C# örnekte bu senaryo gösterilmektedir. İçinde C# yazılmış bir `Sentence` sınıfını tanımlar, belirtilen bir alt dizeyle başlayan bir tümcede bulunan sonraki kelimeyi bulan bir `FindNext` yöntemi içerir. Dize bir başvuru dönüş değeri olarak döndürülür ve yöntemine başvuruya göre geçirilen bir `Boolean` değişkeni, aramanın başarılı olup olmadığını gösterir. Başvuru dönüş değeri, çağıranın yalnızca döndürülen değeri okuyamayacağını belirtir; Ayrıca, bunu değiştirebilir ve bu değişiklik `Sentence` sınıfında dahili olarak bulunan verilere yansıtılır.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Bu durumda başvuru dönüş değerini doğrudan değiştirmek güvenilir değildir, çünkü Yöntem çağrısı bir eşleşme bulamamasına ve tümcedeki ilk sözcüğü döndürmeyebilir. Bu durumda, çağıran, tümcenin ilk sözcüğünü yanlışlıkla değiştirmeyecektir. Bu, çağıran tarafından bir `null` (veya Visual Basic `Nothing` döndüren) tarafından engellenebilir. Ancak bu durumda, değeri `Nothing` olan bir dizeyi değiştirme girişimi bir <xref:System.NullReferenceException> oluşturur. @No__t_0 döndüren çağıran tarafından da engellenebilir, ancak çağıranın değeri <xref:System.String.Empty?displayProperty=nameWithType> bir dize değişkeni tanımlamasına gerek vardır. Çağıran bu dizeyi değiştire, ancak değiştirilen dizenin `Sentence` sınıfı tarafından depolanan tümcedeki sözcüklerle hiçbir ilişkisi olmadığından, değişikliğin kendisi hiçbir amaca hizmet eder.

Bu senaryoyu işlemenin en iyi yolu, başvuru dönüş değerini bir yardımcı yönteme başvuruya göre geçirmektir. Yardımcı yöntemi daha sonra yöntem çağrısının başarılı olup olmadığını ve başvuru dönüş değerini değiştirmek için bir mantığı içerir. Aşağıdaki örnek olası bir uygulama sağlar.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımsız değişkenleri değere ve başvuruya göre geçirme](passing-arguments-by-value-and-by-reference.md)
- [Visual Basic'te Yordamlar](index.md)
