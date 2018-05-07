---
title: (Visual Basic) yansıma kullanarak özniteliklere erişme
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: dca476eef392a2f57d0c66727c53e0e53310d679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>(Visual Basic) yansıma kullanarak özniteliklere erişme
Özel öznitelikler tanımlayın ve bunları kaynak kodunda yerleştirmek olgu ve bu bilgileri alma üzerinde çalışan herhangi bir şekilde olmadan az değerinin olacaktır. Yansıma kullanarak özel öznitelikler içeren tanımlandı bilgi alabilirsiniz. Anahtar yöntemi `GetCustomAttributes`, kaynak kodu özniteliklerinin çalışma zamanı eşdeğerleri olan nesneler dizisi döndürür. Bu yöntem, birden fazla aşırı yüklenmiş sürümlerini içerir. Daha fazla bilgi için bkz. <xref:System.Attribute>.  
  
 Öznitelik belirtimi gibi:  
  
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
  
 Bununla birlikte, kod kadar yürütülmez `SampleClass` öznitelikler için sorgulanır. Çağırma `GetCustomAttributes` üzerinde `SampleClass` neden olan bir `Author` nesnesi oluşturulur ve yukarıdaki olarak başlatıldı. Sınıfın diğer öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur. `GetCustomAttributes` ardından döndürür `Author` nesne ve bir dizi diğer öznitelik nesneleri. Bu dizi yineleme öznitelikleri her dizi öğesi türüne bağlı olarak uygulanan belirlemek ve öznitelik nesnelerden bilgi ayıklamak.  
  
## <a name="example"></a>Örnek  
 Burada, tam bir örnek verilmiştir. Özel bir öznitelik tanımlı, birkaç varlıklara uygulanan ve yansıma alınır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)  
 [Özniteliklerde Depolanan Bilgileri Alma](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Öznitelikler (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [Özel öznitelikler (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
