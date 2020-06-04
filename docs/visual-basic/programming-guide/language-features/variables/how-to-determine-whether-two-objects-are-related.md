---
title: 'Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 30e88a21e737aa57513745899577381ed34151a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410470"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme (Visual Basic)

İki nesneyi, varsa, varsa aralarındaki ilişkiyi belirleyebilir şekilde karşılaştırabilirsiniz. <xref:System.Type.IsInstanceOfType%2A>Sınıfın yöntemi, <xref:System.Type?displayProperty=nameWithType> `True` belirtilen sınıf geçerli sınıftan devralırsa veya geçerli tür belirtilen sınıf tarafından desteklenen bir arabirimse döndürür.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Bir nesnenin başka bir nesnenin sınıfından veya arabiriminden devralıp devrmadığını belirleme

1. Düşündüğünüz nesnede, temel türünde olabilir, <xref:System.Object.GetType%2A> yöntemi çağırın.

2. <xref:System.Type?displayProperty=nameWithType>Tarafından döndürülen nesnedeki <xref:System.Object.GetType%2A> <xref:System.Type.IsInstanceOfType%2A> yöntemi çağırın.

3. İçin bağımsız değişken listesinde <xref:System.Type.IsInstanceOfType%2A> , türetilmiş türden olabileceğini düşündüğünüz nesneyi belirtin.

    <xref:System.Type.IsInstanceOfType%2A>`True`bağımsız değişken türü nesne türünden devralırsa döndürür <xref:System.Type?displayProperty=nameWithType> .

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

Çağrısındaki iki nesne değişkeninin beklenmedik yerleşimini Note <xref:System.Type.IsInstanceOfType%2A> . Beklenen temel tür sınıfı oluşturmak için kullanılır <xref:System.Type?displayProperty=nameWithType> ve beklenen türetilmiş tür yönteme bir bağımsız değişken olarak geçirilir <xref:System.Type.IsInstanceOfType%2A> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)
- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişkeni Değerleri](object-variable-values.md)
- [Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme](how-to-determine-whether-two-objects-are-identical.md)
