---
title: Başvuru dönüş değerleri (Visual Basic)
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: d0600f7d9030324160343e800c37e0f5e68bff61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133984"
---
# <a name="support-for-reference-return-values-visual-basic"></a>Başvuru dönüş değerleri (Visual Basic) için destek

İle başlayarak C# 7.0 C# dili destekleyen *başvuru dönüş değerleri*. Başvuru dönüş değerleri anlamanın tek yolu, bir yönteme başvuru tarafından geçirilen bağımsız değişken karşıtı olmasıdır. Başvuruya göre geçirilen bağımsız değişken değiştirildiğinde değişiklikler çağrı üzerinde değişkeninin değeri yansıtılır. Başvuru dönüş değeri arayan tarafından yapılan değişiklikleri, bir yöntemi çağıran için bir başvuru dönüş değeri sağladığında, çağrılan yöntemin verilerinde yansıtılır.

Visual Basic başvurusu Yazar yöntemleriyle size dönüş değerleri, ancak başvuru dönüş değerleri kullanmasına izin veriyor izin vermez. Diğer bir deyişle, başvuru dönüş değerine sahip bir yöntemi çağırabilir ve bu dönüş değerini değiştirin ve değişiklikleri başvuru dönüş değeri çağrılan yöntemin verileri yansıtılır.

## <a name="modifying-the-ref-return-value-directly"></a>Başvuru dönüş değeri doğrudan değiştirme

Her zaman başarısız ve yok yöntemler için `ByRef` parametreleri, başvuru dönüş değeri doğrudan değiştirebilirsiniz. Başvuru dönüş değeri döndüren ifadeler için yeni değer atayarak bunu yapabilirsiniz. 

Aşağıdaki C# örnek tanımlayan bir `NumericValue.IncrementValue` bir iç değeri artırır ve başvuru olarak döndüren bir yöntem dönüş değeri. 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

Başvuru dönüş değeri Visual Basic aşağıdaki örnekte çağıran tarafından değiştirilir. Unutmayın satırıyla `NumericValue.IncrementValue` yöntem çağrısı bir değer yönteme atamaz. Bunun yerine, yöntem tarafından döndürülen başvuru dönüş değeri için bir değer atar.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>Bir yardımcı yöntemi kullanarak

Diğer durumlarda, bir yöntem çağrısının başvuru dönüş değeri doğrudan değiştirme her zaman istenmeyebilir. Örneğin, bir dize döndüren bir arama yöntemi bir eşleşme her zaman bulamayabilir. Bu durumda, yalnızca arama başarılı olursa, başvuru dönüş değeri değiştirmek istediğiniz.

Aşağıdaki C# örnekte, bu senaryo gösterilmektedir. Tanımladığı bir `Sentence` yazılmış sınıf C# içeren bir `FindNext` sonraki sözcüğe bulur, belirtilen bir alt dizesi ile başlayan bir cümle yöntemi. Bir başvuru döndürmeyi olarak değer ve bir dize döndürülür `Boolean` yönteme başvuru tarafından geçirilen değişkeni arama başarılı olup olmadığını gösterir. Başvuru dönüş değeri, çağırana döndürülen değer yalnızca okunamıyor gösterir. isterse de değiştirebilirsiniz ve bu değişiklik, dahili olarak içinde yer alan verileri yansıtılır `Sentence` sınıfı.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Başvuru doğrudan değiştirme dönüş yöntem çağrısı bir eşleşme bulmak ve cümlede ilk sözcüğün döndürmek başarısız olabilir değer bu durumda güvenilir değildir. Bu durumda, çağıranın yanlışlıkla cümlede ilk sözcüğün değiştirir. Bunu engelleyen döndüren, çağıran tarafından bir `null` (veya `Nothing` Visual Basic'te). Ancak bu durumda, değeri olan bir dize değiştirmeye `Nothing` oluşturur bir <xref:System.NullReferenceException>. Ayrıca döndüren, çağıran tarafından engellendi, <xref:System.String.Empty?displayProperty=nameWithType>, ancak bu çağrıyı değeri bir dize değişkeni tanımlamanızı gerektirir <xref:System.String.Empty?displayProperty=nameWithType>. Çağıranın bu dizeyi değiştirebilirsiniz, ancak değiştirilen dize tarafından depolanan tümcedeki sözcükleri hiçbir ilişkisi olduğundan değişiklik herhangi bir amacı, hizmet `Sentence` sınıfı.

Bu senaryonun işlenmesi için en iyi yolu, bir yardımcı yöntem başvuruya başvuru dönüş değeri geçirmektir. Yardımcı yöntemi, ardından yöntem çağrısının başarılı olduğunu olsaydı, değiştirmek için başvuru dönen değer olup olmadığını ve belirlemek için mantığı içerir. Aşağıdaki örnekte, olası bir uygulamasını sağlar.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımsız değişkenleri değere ve başvuruya göre geçirme](passing-arguments-by-value-and-by-reference.md)
- [Visual Basic'te Yordamlar](index.md)
