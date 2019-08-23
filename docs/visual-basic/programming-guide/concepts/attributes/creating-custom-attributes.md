---
title: Özel öznitelikler oluşturma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: e4b55f92466fde47011937d08c946c9c75ca07b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966327"
---
# <a name="creating-custom-attributes-visual-basic"></a>Özel öznitelikler oluşturma (Visual Basic)
Doğrudan veya dolaylı <xref:System.Attribute>olarak sınıfından türetilmiş bir sınıf olan öznitelik sınıfını tanımlayarak kendi özel öznitelerinizi oluşturabilirsiniz. Bu, meta verilerde hızlı ve kolay bir şekilde öznitelik tanımları tanımlamayı sağlar. Türleri, türünü yazan programcının adıyla etiketlemek istediğinizi varsayalım. Özel `Author` bir öznitelik sınıfı tanımlayabilirsiniz:  
  
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
  
 Sınıf adı özniteliğin adıdır, `Author`. Öğesinden `System.Attribute`türetilir, bu nedenle özel bir öznitelik sınıfıdır. Oluşturucunun parametreleri özel özniteliğin konumsal parametreleridir. Bu örnekte, `name` bir Konumsal parametredir. Tüm genel okuma/yazma alanları veya özellikleri parametreler olarak adlandırılır. Bu durumda, `version` tek adlandırılmış parametredir. Özniteliği yalnızca sınıf ve `AttributeUsage` `Structure` bildirimlerde geçerli `Author` hale getirmek için özniteliğinin kullanımını unutmayın.  
  
 Bu yeni özniteliği şu şekilde kullanabilirsiniz:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage`, özel bir özniteliği tek `AllowMultiple`kullanımı veya çok kullanımı yapabileceğiniz adlandırılmış bir parametreye sahiptir. Aşağıdaki kod örneğinde, Multiuse özniteliği oluşturulur.  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 Aşağıdaki kod örneğinde, aynı türde birden çok öznitelik bir sınıfa uygulanır.  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
> Öznitelik sınıfınız bir özellik içeriyorsa, bu özellik oku-yaz olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
- [Özel Öznitelikler Yazma](../../../../standard/attributes/writing-custom-attributes.md)
- [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Öznitelikler (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Yansıma kullanarak özniteliklere erişme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
