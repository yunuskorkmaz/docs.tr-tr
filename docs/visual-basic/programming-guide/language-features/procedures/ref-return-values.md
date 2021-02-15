---
description: 'Hakkında daha fazla bilgi edinin: başvuru dönüş değerleri için destek (Visual Basic)'
title: Başvuru dönüş değerleri
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: 215a647c68eb7eadd394a1a7842ceb98c46e04a5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466555"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Başvuru dönüş değerleri için destek (Visual Basic)

C# 7,0 ile başlayarak, C# dili *Başvuru dönüş değerlerini* destekler. Başvuru dönüş değerlerini anlamanın bir yolu, bir yönteme başvuruya göre geçirilen bağımsız değişkenlerin tersidir. Başvuruya göre geçirilen bir bağımsız değişken değiştirildiğinde, değişiklikler çağıranın değişkeninin değerine yansıtılır. Bir yöntem bir çağırana bir başvuru dönüş değeri sağlıyorsa, çağıran tarafından başvuru dönüş değeri yapılan değişiklikler çağrılan metodun verilerinde yansıtılır.

Visual Basic, başvuru dönüş değerleri olan Yöntemler yazmanıza izin vermez, ancak başvuru dönüş değerlerini kullanmanıza izin verir. Diğer bir deyişle, başvuru dönüş değeri olan bir yöntemi çağırabilir ve bu dönüş değerini değiştirebilir ve başvuru dönüş değerindeki değişiklikler çağrılan metodun verilerinde yansıtılır.

## <a name="modifying-the-ref-return-value-directly"></a>Başvuru dönüş değerini doğrudan değiştirme

Her zaman başarılı olan ve parametresi olmayan yöntemler için `ByRef` Başvuru dönüş değerini doğrudan değiştirebilirsiniz. Bunu, başvuru dönüş değeri döndüren deyimlere yeni değeri atayarak yapabilirsiniz.

Aşağıdaki C# örneği, bir `NumericValue.IncrementValue` iç değeri artıran ve başvuru dönüş değeri olarak döndüren bir yöntemi tanımlar.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Başvuru dönüş değeri daha sonra aşağıdaki Visual Basic örneğinde çağıran tarafından değiştirilir. `NumericValue.IncrementValue`Yöntem çağrısını içeren satırın yöntemine bir değer atamayacağını unutmayın. Bunun yerine, yöntemi tarafından döndürülen başvuru dönüş değerine bir değer atar.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Yardımcı yöntemi kullanma

Diğer durumlarda, doğrudan yöntem çağrısının başvuru dönüş değerini değiştirmek her zaman istenmeyebilir. Örneğin, bir dize döndüren arama yöntemi her zaman bir eşleşme bulmayabilir. Bu durumda, başvuru dönüş değerini yalnızca arama başarılı olursa değiştirmek istersiniz.

Aşağıdaki C# örneği bu senaryoyu göstermektedir. C# dilinde yazılmış bir sınıfı tanımlar, belirtilen bir alt `Sentence` `FindNext` dizeyle başlayan bir tümcede bulunan sonraki kelimeyi bulan bir yöntemi içerir. Dize bir başvuru dönüş değeri olarak döndürülür ve `Boolean` yöntemine başvuruya göre geçirilen bir değişken aramanın başarılı olup olmadığını gösterir. Başvuru dönüş değeri, döndürülen değeri okumayla ilgili ek olarak, çağıranın da değiştiremeyeceğini ve bu değişikliğin sınıfta dahili olarak bulunan verilere yansıtıldığını gösterir `Sentence` .

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Bu durumda başvuru dönüş değerini doğrudan değiştirmek güvenilir değildir, çünkü Yöntem çağrısı bir eşleşme bulamamasına ve tümcedeki ilk sözcüğü döndürmeyebilir. Bu durumda, çağıran, tümcenin ilk sözcüğünü yanlışlıkla değiştirmeyecektir. Bu, çağıran tarafından `null` (veya Visual Basic) döndürülürken engellenebilir `Nothing` . Ancak bu durumda, değeri bir olan bir dizeyi değiştirme girişimi `Nothing` <xref:System.NullReferenceException> . Çağıran tarafından da engellenebilir <xref:System.String.Empty?displayProperty=nameWithType> , ancak bu, çağıranın değeri olan bir dize değişkeni tanımlamasına gerek duyar <xref:System.String.Empty?displayProperty=nameWithType> . Çağıran bu dizeyi değiştire, ancak değiştirilen dizenin sınıf tarafından depolanan tümcedeki sözcüklerle hiçbir ilişkisi olmadığından, değişikliğin kendisi bir amaca hizmet eder `Sentence` .

Bu senaryoyu işlemenin en iyi yolu, başvuru dönüş değerini bir yardımcı yönteme başvuruya göre geçirmektir. Yardımcı yöntemi daha sonra yöntem çağrısının başarılı olup olmadığını ve başvuru dönüş değerini değiştirmek için bir mantığı içerir. Aşağıdaki örnek olası bir uygulama sağlar.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımsız değişkenleri değere ve başvuruya göre geçirme](passing-arguments-by-value-and-by-reference.md)
- [Visual Basic'te Yordamlar](index.md)
