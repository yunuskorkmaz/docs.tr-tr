---
title: Ref İade Değerleri
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: f2a92c584dbb12a322e28435d797fa4d7c2f6dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186931"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Referans döndürme değerleri desteği (Visual Basic)

C# 7.0 ile başlayarak, C# dili *referans dönüş değerlerini*destekler. Başvuru döndürme değerlerini anlamanın bir yolu, bir yönteme başvuruyla geçirilen bağımsız değişkenlerin zıttı olmalarıdır. Başvuru tarafından geçirilen bir bağımsız değişken değiştirildiğinde, değişiklikler arayan değişkenin değerine yansıtılır. Bir yöntem arayana bir referans iade değeri sağladığında, arayan tarafından referans iade değerine yapılan değişiklikler çağrılan yöntemin verilerine yansıtılır.

Visual Basic, başvuru iade değerleriyle yöntemler yazmanıza izin vermez, ancak başvuru döndürme değerlerini tüketmenize olanak sağlar. Başka bir deyişle, bir başvuru iade değeri ile bir yöntem çağırabilir ve bu döndürme değeri değiştirebilirsiniz ve referans dönüş değeri değişiklikleri çağrılan yöntemin verilerine yansıtılır.

## <a name="modifying-the-ref-return-value-directly"></a>Ref iade değerinin doğrudan değiştirilmesi

Her zaman başarılı olan `ByRef` ve parametreleri olmayan yöntemler için, başvuru iade değerini doğrudan değiştirebilirsiniz. Bunu, başvuru iade değerini döndüren ifadelere yeni değer atayarak yaparsınız.

Aşağıdaki C# örneği, `NumericValue.IncrementValue` iç değer insidansını artımlı ve referans getiri değeri olarak döndüren bir yöntem tanımlar.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Başvuru iade değeri daha sonra aşağıdaki Visual Basic örneğinde arayan tarafından değiştirilir. Yöntem çağrısı yla `NumericValue.IncrementValue` gelen satırın yönteme bir değer atamadığını unutmayın. Bunun yerine, yöntem tarafından döndürülen başvuru iade değerine bir değer atar.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Yardımcı yöntemi kullanma

Diğer durumlarda, bir yöntem çağrısının referans iade değerini doğrudan değiştirmek her zaman istenmeyebilir. Örneğin, dize döndüren bir arama yöntemi her zaman eşleşme bulmayabilir. Bu durumda, yalnızca arama başarılı olursa başvuru iade değerini değiştirmek istiyorsunuz.

Aşağıdaki C# örneği bu senaryoyu göstermektedir. C# ile `Sentence` yazılmış bir sınıfı `FindNext` tanımlar, bir sonraki sözcüğü belirli bir alt dizeyle başlayan bir cümlede bulan bir yöntem içerir. Dize bir başvuru dönüş değeri olarak `Boolean` döndürülür ve yönteme başvuru ile geçirilen bir değişken aramanın başarılı olup olmadığını gösterir. Başvuru iade değeri, döndürülen değeri okumanın yanı sıra, arayanın da değiştirebileceğini ve bu değişikliğin `Sentence` sınıfta dahili olarak bulunan verilere yansıttığını gösterir.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Yöntem çağrısı eşleşmeyi bulup cümledeki ilk sözcüğü döndürebileceğinden, bu durumda referans iade değerini doğrudan değiştirmek güvenilir değildir. Bu durumda, arayan yanlışlıkla cümlenin ilk sözcük değiştirecektir. Bu, arayanın (veya `null` `Nothing` Visual Basic'te) döndürülmesi yle önlenebilir. Ancak bu durumda, değeri `Nothing` bir <xref:System.NullReferenceException>. Arayan tarafından <xref:System.String.Empty?displayProperty=nameWithType>da engellenebilirse, ancak bu, arayanın değeri <xref:System.String.Empty?displayProperty=nameWithType>. Arayan bu dizeyi değiştirebilse de, değiştirilen dize `Sentence` sınıf tarafından depolanan tümcedeki sözcüklerle hiçbir ilişkisi olmadığından, değişikliğin kendisi hiçbir amaca hizmet etmez.

Bu senaryoyu işlemenin en iyi yolu, başvuru iade değerini bir yardımcı yöntemine başvuru yaparak geçirmektir. Yardımcı yöntemi daha sonra yöntem çağrısının başarılı olup olmadığını belirlemek ve varsa, başvuru iade değerini değiştirmek için mantık içerir. Aşağıdaki örnek olası bir uygulama sağlar.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımsız değişkenleri değere ve başvuruya göre geçirme](passing-arguments-by-value-and-by-reference.md)
- [Visual Basic'te Yordamlar](index.md)
