---
title: 'Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: b3f5fc017166ba9cf28359db5de850c81b73bd69
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348623"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme (Visual Basic)

İki nesneyi, varsa, varsa aralarındaki ilişkiyi belirleyebilir şekilde karşılaştırabilirsiniz. <xref:System.Type?displayProperty=nameWithType> sınıfının <xref:System.Type.IsInstanceOfType%2A> yöntemi, belirtilen sınıf geçerli sınıftan devralırsa veya geçerli tür belirtilen sınıf tarafından desteklenen bir arabirimse `True` döndürüyor.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Bir nesnenin başka bir nesnenin sınıfından veya arabiriminden devralıp devrmadığını belirleme

1. Düşündüğünüz nesnede, temel türde olabilir <xref:System.Object.GetType%2A> yöntemi çağırın.

2. <xref:System.Object.GetType%2A>tarafından döndürülen <xref:System.Type?displayProperty=nameWithType> nesnesinde <xref:System.Type.IsInstanceOfType%2A> yöntemini çağırın.

3. <xref:System.Type.IsInstanceOfType%2A>için bağımsız değişken listesinde, türetilmiş türden olabileceğini düşündüğünüz nesneyi belirtin.

    bağımsız değişken türü <xref:System.Type?displayProperty=nameWithType> nesne türünden devralırsa <xref:System.Type.IsInstanceOfType%2A> `True` döndürür.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir nesnenin başka bir nesnenin sınıfından türetilmiş bir sınıfı temsil edip etmediğini belirler.

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

<xref:System.Type.IsInstanceOfType%2A>çağrısında iki nesne değişkeninin beklenmedik yerleşimini aklınızda edin. Beklenen temel tür, <xref:System.Type?displayProperty=nameWithType> sınıfını oluşturmak için kullanılır ve beklenen türetilmiş tür <xref:System.Type.IsInstanceOfType%2A> yöntemine bir bağımsız değişken olarak geçirilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
