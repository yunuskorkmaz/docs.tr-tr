---
title: "Özel öznitelikler (Visual Basic) oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a24553ae4cc2186e805d76ddb37f38c0322aeac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 `AttributeUsage`adlandırılmış bir parametre içeriyor `AllowMultiple`, özel bir öznitelik tek kullanımlık veya multiuse yapabileceğiniz ile. Aşağıdaki kod örneğinde multiuse özniteliği oluşturulur.  
  
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
 [Özel öznitelikler yazma](../../../../standard/attributes/writing-custom-attributes.md)  
 [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Öznitelikler (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [(Visual Basic) yansıma kullanarak özniteliklere erişme](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
