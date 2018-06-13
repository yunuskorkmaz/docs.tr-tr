---
title: Özel öznitelikler (Visual Basic) oluşturma
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 9af0832e04308bf1942fc955afe5a67161096465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642899"
---
# <a name="creating-custom-attributes-visual-basic"></a>Özel öznitelikler (Visual Basic) oluşturma
Doğrudan veya dolaylı olarak türeyen bir sınıf bir öznitelik sınıfı tanımlayarak, kendi özel öznitelikler oluşturabilirsiniz <xref:System.Attribute>, hızlı ve kolay meta verilerde özniteliği tanımlarını tanımlayan hangi yapar. Etiket türleri türü yazan programcı için adıyla istediğinizi varsayalım. Özel bir tanımlayabilir `Author` öznitelik sınıfı:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 Sınıf adı özniteliğin adıdır `Author`. Öğesinden türetilen `System.Attribute`özel bir öznitelik sınıfı gelir. Oluşturucusu ait, özel özniteliğin konumsal parametreler parametreleridir. Bu örnekte, `name` konumsal bir parametredir. Herhangi bir genel okuma-yazma alanlar veya özellikler parametreleri olarak adlandırılır. Bu durumda, `version` tek parametresi olarak adlandırılır. Kullanımına dikkat edin `AttributeUsage` yapmak için öznitelik `Author` özniteliği yalnızca sınıfında geçerli ve `Structure` bildirimleri.  
  
 Bu yeni öznitelik aşağıdaki gibi kullanabilirsiniz:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage` adlandırılmış bir parametre içeriyor `AllowMultiple`, özel bir öznitelik tek kullanımlık veya multiuse yapabileceğiniz ile. Aşağıdaki kod örneğinde multiuse özniteliği oluşturulur.  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 Aşağıdaki kod örneğinde aynı türde birden çok öznitelik bir sınıfa uygulanır.  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  Öznitelik sınıfı bir özellik varsa, bu özelliği oku-yaz olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection>  
 [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)  
 [Özel Öznitelikler Yazma](../../../../standard/attributes/writing-custom-attributes.md)  
 [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Öznitelikler (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [(Visual Basic) yansıma kullanarak özniteliklere erişme](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
