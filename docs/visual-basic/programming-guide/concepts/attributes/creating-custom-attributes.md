---
title: Özel Öznitelikler Oluşturma
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 84b400c2fa1b2d4019eec32092f954d680e64978
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400700"
---
# <a name="creating-custom-attributes-visual-basic"></a>Özel öznitelikler oluşturma (Visual Basic)

Doğrudan veya dolaylı olarak sınıfından türetilmiş bir sınıf olan öznitelik sınıfını tanımlayarak kendi özel öznitelerinizi oluşturabilirsiniz <xref:System.Attribute> . Bu, meta verilerde hızlı ve kolay bir şekilde öznitelik tanımları tanımlamayı sağlar. Türleri, türünü yazan programcının adıyla etiketlemek istediğinizi varsayalım. Özel bir `Author` öznitelik sınıfı tanımlayabilirsiniz:

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

Sınıf adı özniteliğin adıdır, `Author` . Öğesinden türetilir `System.Attribute` , bu nedenle özel bir öznitelik sınıfıdır. Oluşturucunun parametreleri özel özniteliğin konumsal parametreleridir. Bu örnekte, `name` bir Konumsal parametredir. Tüm genel okuma/yazma alanları veya özellikleri parametreler olarak adlandırılır. Bu durumda, `version` tek adlandırılmış parametredir. Özniteliği `AttributeUsage` `Author` yalnızca sınıf ve bildirimlerde geçerli hale getirmek için özniteliğinin kullanımını unutmayın `Structure` .

Bu yeni özniteliği şu şekilde kullanabilirsiniz:

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

`AttributeUsage`, `AllowMultiple` özel bir özniteliği tek kullanımı veya çok kullanımı yapabileceğiniz adlandırılmış bir parametreye sahiptir. Aşağıdaki kod örneğinde, Multiuse özniteliği oluşturulur.

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
- [Visual Basic Programlama Kılavuzu](../../index.md)
- [Özel Öznitelikler Yazma](../../../../standard/attributes/writing-custom-attributes.md)
- [Yansıma (Visual Basic)](../reflection.md)
- [Öznitelikler (Visual Basic)](../../../language-reference/attributes.md)
- [Yansıma kullanarak özniteliklere erişme (Visual Basic)](accessing-attributes-by-using-reflection.md)
- [AttributeUsage (Visual Basic)](attributeusage.md)
