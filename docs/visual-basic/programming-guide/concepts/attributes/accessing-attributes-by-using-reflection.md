---
title: (Visual Basic) yansıma kullanarak özniteliklere erişme
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: e5cbce8529cc7554a8edacb2d83dabb73a495eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937164"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>(Visual Basic) yansıma kullanarak özniteliklere erişme
Özel öznitelikler tanımlamak ve bunları kaynak kodunuzu getirin olgu üzerinde çalışan ve bu bilgileri alınırken bir şekilde olmadan küçük değer olacaktır. Yansıma kullanarak özel öznitelik tanımlandı bilgi alabilirsiniz. Anahtar yöntemi `GetCustomAttributes`, kaynak kod özniteliklerini çalışma zamanı eşdeğerleri olan nesneler dizisi döndürür. Bu yöntem, birden fazla aşırı yüklenmiş sürümleri vardır. Daha fazla bilgi için bkz. <xref:System.Attribute>.  
  
 Bir öznitelik belirtimi gibi:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 Bunun için kavramsal olarak eşdeğerdir:  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 Ancak, kod kadar yürütülmez `SampleClass` öznitelikleri için sorgulanır. Çağırma `GetCustomAttributes` üzerinde `SampleClass` neden olan bir `Author` nesne oluşturulur ve yukarıdaki gibi başlatıldı. Sınıfın diğer öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur. `GetCustomAttributes` ardından döndürür `Author` ve diğer öznitelik nesneleri bir dizideki nesne. Bu dizi yineleme hangi özniteliklerin her dizi öğesi türüne bağlı olarak uygulanan belirlemek ve öznitelik nesnelerden bilgiler ayıklayın.  
  
## <a name="example"></a>Örnek  
 Tam bir örnek aşağıda verilmiştir. Özel bir öznitelik tanımlı, birden fazla varlıklarına uygulanan ve yansıma alınır.  
  
```vb  
' Multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
  
        ' Default value  
        version = 1.0  
    End Sub  
  
    Function GetName() As String  
        Return name  
    End Function          
End Class  
  
' Class with the Author attribute  
<Author("P. Ackerman")>   
Public Class FirstClass  
End Class  
  
' Class without the Author attribute  
Public Class SecondClass  
End Class  
  
' Class with multiple Author attributes.  
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>   
Public Class ThirdClass  
End Class  
  
Class TestAuthorAttribute  
    Sub Main()  
        PrintAuthorInfo(GetType(FirstClass))  
        PrintAuthorInfo(GetType(SecondClass))  
        PrintAuthorInfo(GetType(ThirdClass))  
    End Sub  
  
    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)  
        System.Console.WriteLine("Author information for {0}", t)  
  
        ' Using reflection  
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)  
  
        ' Displaying output  
        For Each attr In attrs  
            Dim a As Author = CType(attr, Author)  
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)  
        Next              
    End Sub  
  
    ' Output:  
    '   Author information for FirstClass  
    '     P. Ackerman, version 1.00  
    ' Author information for SecondClass  
    ' Author information for ThirdClass  
    '  R. Koch, version 2.00  
    '  P. Ackerman, version 1.00  
  
End Class  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
- [Özniteliklerde Depolanan Bilgileri Alma](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Öznitelikler (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Özel öznitelikler (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
