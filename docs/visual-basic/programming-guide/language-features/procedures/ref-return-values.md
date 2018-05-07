---
title: Ref dönüş değerleri (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2979359f0ffafe46a62696485bbb87b211c1704
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="support-for-reference-return-values-visual-basic"></a>Başvuru dönüş değerleri (Visual Basic) desteği

C# 7. 0'dan başlayarak, C# dili destekleyen *başvuru dönüş değerleri*. Başvuru dönüş değerleri anlamak için bir yönteme başvurusu tarafından geçirilen bağımsız değişken karşıtı oldukları yoludur. Başvuruya göre geçirilen bağımsız değişken değiştirildiğinde, değişiklikler üzerinde çağıran değişkeninin değeri yansıtılır. Bir yöntem için çağıran bir başvuru dönüş değeri sağladığında, başvuru dönüş değeri çağıran tarafından yapılan değişiklikler çağrılan yöntemin verilerine yansıtılır.

Visual Basic başvurusu Yazar yöntemleriyle size dönüş değerleri, ancak başvuru dönüş değerlerini kullanmasına izin veriyor izin vermiyor. Diğer bir deyişle, başvuru dönüş değeri olan bir yöntemini çağırın ve o dönüş değerini değiştirin ve değişiklikleri başvuru dönüş değeri için çağrılan yöntemin verilerde yansıtılır.

## <a name="modifying-the-ref-return-value-directly"></a>Ref dönüş değeri doğrudan değiştirme

Her zaman başarılı ve yok yöntemleri için `ByRef` parametreleri, başvuru dönüş değeri doğrudan değiştirebilirsiniz. Başvuru dönüş değeri döndüren ifadeler için yeni değer atayarak bunu yapabilirsiniz. 

Aşağıdaki C# örnek tanımlayan bir `NumericValue.IncrementValue` bir iç değer artırır ve bir başvuru olarak döndüren yöntemi dönüş değeri. 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Başvuru dönüş değeri sonra aşağıdaki Visual Basic örnekte çağıran tarafından değiştirildi. Unutmayın satırıyla `NumericValue.IncrementValue` yöntem çağrısı yöntemi bir değer atamaz. Bunun yerine, yöntem tarafından döndürülen başvuru dönüş değeri için bir değer atar.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Yardımcı yöntemi kullanarak

Diğer durumlarda, yöntem çağrısı başvuru dönüş değerini doğrudan değiştirme her zaman tercih edilebilir değil. Örneğin, bir dize döndürür. search yöntemini bir eşleşme her zaman bulamayabilir. Bu durumda, yalnızca arama başarılı olduğunda başvuru dönüş değerini değiştirmek istediğiniz.

Bu senaryo aşağıdaki C# örnek gösterilmektedir. Tanımladığı bir `Sentence` C# ile yazılmış sınıfı içeren bir `FindNext` belirtilen bir alt dizesi ile başlayan bir tümcedeki sonraki sözcüğü bulur yöntemi. Bir başvuru döndürmek gibi değer ve bir dize döndürdü `Boolean` başvuruya yöntemine geçirilen değişken gösterir arama başarılı olup olmadığını. Başvuru dönüş değeri çağıran yalnızca döndürülen değeri okunamıyor gösterir; çözemiyorsa de değiştirebilirsiniz ve bu değişikliği dahili içinde yer alan verileri yansıtılır `Sentence` sınıfı.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Doğrudan başvuru değiştirme Döndür bir eşleşme bulmak ve cümlede ilk sözcük dönmek yöntem çağrısı başarısız olabilir beri değeri bu durumda güvenilir değil. Bu durumda, çağıranın yanlışlıkla tümcenin ilk word değiştirecektir. Bu döndürme çağıran tarafından engelledi bir `null` (veya `Nothing` Visual Basic'te). Ancak bu durumda, değeri olan bir dize değiştirilmeye çalışılıyor `Nothing` oluşturur bir <xref:System.NullReferenceException>. Döndürme çağıran tarafından da engelledi, <xref:System.String.Empty?displayProperty=nameWithType>, ancak bu çağrıyı değeri bir dize değişkeni tanımlamanızı gerektirir <xref:System.String.Empty?displayProperty=nameWithType>. Çağıranın bu dizeyi değiştirebilirsiniz, ancak değiştirilen dizesi tarafından depolanan tümcedeki sözcükleri ilişkisi olduğundan değişiklik herhangi bir amacı hizmet `Sentence` sınıfı.

Bu senaryo işlemek için en iyi yolu, bir yardımcı yöntem başvuru tarafından başvuru dönüş değeri geçirmektir. Yardımcı yöntemi, daha sonra yöntem çağrısı başarılı oldu ve olsaydı, değiştirmek için başvuru dönen değer olup olmadığını belirlemek için mantığı içerir. Aşağıdaki örnek, olası bir uygulamasını sağlar.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

[Bağımsız değişkenleri değere ve başvuruya göre geçirme](passing-arguments-by-value-and-by-reference.md)   
[Visual Basic'te Yordamlar](index.md)   


