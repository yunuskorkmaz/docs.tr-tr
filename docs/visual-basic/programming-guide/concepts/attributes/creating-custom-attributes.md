---
title: Özel öznitelikler (Visual Basic) oluşturma
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 90e8e9b9a3fa8e0b488f41d035b017d6113213b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903558"
---
# <a name="creating-custom-attributes-visual-basic"></a>Özel öznitelikler (Visual Basic) oluşturma
Bir öznitelik sınıfı doğrudan veya dolaylı olarak türetildiği bir sınıf tanımlayarak kendi özel öznitelikler oluşturabilir <xref:System.Attribute>, hızlı ve kolay meta veri özniteliği tanımlarını tanımlayan hale getirir. Etiket türlerine türü yazan Programcı adıyla istediğinizi varsayalım. Özel bir tanımlayabilir `Author` öznitelik sınıfı:  
  
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
  
 Özniteliğin adı, sınıf adıdır `Author`. Öğesinden türetilen `System.Attribute`, bir özel öznitelik sınıfı olduğu için. Özel özniteliğin konumsal parametreler oluşturucunun parametrelerdir. Bu örnekte, `name` konumsal bir parametredir. Parametreleri, tüm genel okuma-yazma alanlar ve Özellikler adlandırılır. Bu durumda, `version` tek parametre olarak adlandırılır. Kullanımına dikkat edin `AttributeUsage` yapmak için özniteliği `Author` özniteliği yalnızca sınıf geçerli ve `Structure` bildirimleri.  
  
 Bu yeni bir öznitelik şu şekilde kullanabilirsiniz:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage` adlandırılmış bir parametreye sahip `AllowMultiple`, özel bir öznitelik tek kullanımlık veya multiuse yapabileceğiniz ile. Aşağıdaki kod örneğinde multiuse özniteliği oluşturulur.  
  
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
>  Öznitelik sınıfı bir özellik içeriyorsa, bu özellik salt okunur olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
- [Özel Öznitelikler Yazma](../../../../standard/attributes/writing-custom-attributes.md)
- [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Öznitelikler (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [(Visual Basic) yansıma kullanarak özniteliklere erişme](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
