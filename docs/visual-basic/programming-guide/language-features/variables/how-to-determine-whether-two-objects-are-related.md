---
title: 'Nasıl yapılır: Iki nesnenin Ilgili olup olmadığını belirleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626559"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Nasıl yapılır: Iki nesnenin Ilgili olup olmadığını belirleme (Visual Basic)

İki nesneyi, varsa, varsa aralarındaki ilişkiyi belirleyebilir şekilde karşılaştırabilirsiniz. Sınıfın yöntemi, belirtilen sınıf geçerli sınıftan devralırsa veya geçerli tür belirtilen sınıf tarafından desteklenen bir arabirimse döndürür `True`. <xref:System.Type.IsInstanceOfType%2A> <xref:System.Type?displayProperty=nameWithType>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Bir nesnenin başka bir nesnenin sınıfından veya arabiriminden devralıp devrmadığını belirleme

1. Düşündüğünüz nesnede, temel türünde olabilir, <xref:System.Object.GetType%2A> yöntemi çağırın.

2. <xref:System.Type.IsInstanceOfType%2A> Tarafından <xref:System.Type?displayProperty=nameWithType> döndürülen<xref:System.Object.GetType%2A>nesnedeki yöntemi çağırın.

3. İçin <xref:System.Type.IsInstanceOfType%2A>bağımsız değişken listesinde, türetilmiş türden olabileceğini düşündüğünüz nesneyi belirtin.

    <xref:System.Type.IsInstanceOfType%2A>bağımsız `True` değişken türü <xref:System.Type?displayProperty=nameWithType> nesne türünden devralırsa döndürür.

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

Çağrısındaki iki nesne değişkeninin beklenmedik yerleşimini Note <xref:System.Type.IsInstanceOfType%2A>. Beklenen temel tür <xref:System.Type?displayProperty=nameWithType> sınıfı oluşturmak için kullanılır ve beklenen türetilmiş tür <xref:System.Type.IsInstanceOfType%2A> yönteme bir bağımsız değişken olarak geçirilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Nasıl yapılır: Iki nesnenin aynı olup olmadığını belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
