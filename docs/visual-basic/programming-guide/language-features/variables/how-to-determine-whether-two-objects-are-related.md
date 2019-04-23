---
title: 'Nasıl yapılır: İki nesnenin ilgili olup olmadığını belirleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: f59e00d80d28fc4bf24874d25b5c12643649c834
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342108"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Nasıl yapılır: İki nesnenin ilgili olup olmadığını belirleme (Visual Basic)
İki nesne varsa, oluşturuldukları sınıflar arasındaki ilişkileri belirlemek için karşılaştırabilirsiniz. <xref:System.Type.IsInstanceOfType%2A> Yöntemi <xref:System.Type?displayProperty=nameWithType> sınıfı döndürür `True` belirtilen sınıf geçerli sınıfından devralan veya geçerli türü belirtilen sınıfı tarafından desteklenen bir arabirimdir.  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Bir nesne başka bir nesnenin sınıfı veya arabirimi devralır belirlemek için  
  
1. Düşündüğünüz nesnesinde, temel türünde, çağırma <xref:System.Object.GetType%2A> yöntemi.  
  
2. Üzerinde <xref:System.Type?displayProperty=nameWithType> tarafından döndürülen nesne <xref:System.Object.GetType%2A>, çağırma <xref:System.Type.IsInstanceOfType%2A> yöntemi.  
  
3. Bağımsız değişken listesinde <xref:System.Type.IsInstanceOfType%2A>, düşündüğünüz nesne, türetilmiş bir tür olabilir belirtin.  
  
     <xref:System.Type.IsInstanceOfType%2A> döndürür `True` bağımsız değişken türünü öğesinden devralıyorsa <xref:System.Type?displayProperty=nameWithType> nesne türü.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir nesne başka bir nesnenin sınıfından türetilen bir sınıf temsil edip etmediğini belirler.  
  
```  
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
  
 İki nesne değişkenleri aramasında beklenmeyen yerleşimini unutmayın <xref:System.Type.IsInstanceOfType%2A>. Beklenen temel türünü oluşturmak için kullanılan <xref:System.Type?displayProperty=nameWithType> sınıfı ve beklenen türetilmiş bir tür bağımsız değişkeni olarak geçirilir <xref:System.Type.IsInstanceOfType%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Nasıl yapılır: İki nesnenin aynı olup olmadığını belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
