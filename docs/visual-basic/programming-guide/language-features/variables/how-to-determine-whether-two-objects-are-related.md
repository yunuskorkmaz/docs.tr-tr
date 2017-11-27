---
title: "Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7824742459fca355c0043ad8ed20a26330402c05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme (Visual Basic)
Varsa, oluşturuldukları sınıflar arasındaki ilişkiyi belirlemek için iki nesne karşılaştırabilirsiniz. <xref:System.Type.IsInstanceOfType%2A> Yöntemi <xref:System.Type?displayProperty=nameWithType> sınıf döndürür `True` belirtilen sınıf geçerli sınıfından devralan veya geçerli türü belirtilen sınıfı tarafından desteklenen bir arabirimdir.  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Bir nesne başka bir nesnenin sınıf veya arabirim devralır belirlemek için  
  
1.  Düşündüğünüz bir nesne üzerinde taban türü olamaz, çağırma <xref:System.Object.GetType%2A> yöntemi.  
  
2.  Üzerinde <xref:System.Type?displayProperty=nameWithType> tarafından döndürülen nesne <xref:System.Object.GetType%2A>, çağırma <xref:System.Type.IsInstanceOfType%2A> yöntemi.  
  
3.  İçin bağımsız değişken listesinde <xref:System.Type.IsInstanceOfType%2A>, düşündüğünüz nesnesi, türetilen tür olabilir belirtin.  
  
     <xref:System.Type.IsInstanceOfType%2A>döndürür `True` kendi bağımsız değişken türü devraldığı varsa <xref:System.Type?displayProperty=nameWithType> nesne türü.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir nesne başka bir nesnenin sınıfından türetilen bir sınıfı temsil edip etmediğini belirler.  
  
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
  
 İki nesne değişkenleri çağrısında beklenmeyen yerleşimini Not <xref:System.Type.IsInstanceOfType%2A>. Beklenen temel türü oluşturmak için kullanılan <xref:System.Type?displayProperty=nameWithType> sınıfı ve beklenen türetilen tür bağımsız değişkeni olarak geçirilir <xref:System.Type.IsInstanceOfType%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [Nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Nesne değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne değişkeni değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Nasıl yapılır: iki nesnenin aynı olup olmadığını belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
