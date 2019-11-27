---
title: Yansıma Kullanarak Özniteliklere Erişme
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: 94352f07cf1f7e4a35f023503f138596ae5ac227
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353550"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Yansıma kullanarak özniteliklere erişme (Visual Basic)

Özel öznitelikleri tanımlayabilir ve bunları kaynak kodunuza yerleştirebilirsiniz. Bu bilgiler, bu bilgileri alma ve üzerinde işlem yapmaya gerek kalmadan çok az değer elde edebilir. Yansıma kullanarak özel özniteliklerle tanımlanan bilgileri alabilirsiniz. Anahtar yöntemi, kaynak kodu özniteliklerinin çalışma zamanı eşdeğerleri olan nesnelerin bir dizisini döndüren `GetCustomAttributes`. Bu yöntemin birkaç aşırı yüklü sürümü vardır. Daha fazla bilgi için bkz. <xref:System.Attribute>.

Şöyle bir öznitelik belirtimi:

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 kavramsal olarak eşdeğerdir:

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

Ancak, `SampleClass` öznitelikler için sorgulanana kadar kod yürütülmez. `SampleClass` `GetCustomAttributes` çağırmak `Author` nesnenin yukarıda olarak oluşturulmasına ve başlatılmasına neden olur. Sınıfın başka öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur. `GetCustomAttributes` sonra `Author` nesnesini ve dizideki diğer öznitelik nesnelerini döndürür. Daha sonra bu dizinin üzerinde yineleyebilir, her bir dizi öğesinin türüne göre hangi özniteliklerin uygulandığını belirleyebilir ve öznitelik nesnelerinden bilgi ayıklayabilirsiniz.

## <a name="example"></a>Örnek

Aşağıda bir örnek verilmiştir. Özel bir öznitelik tanımlanır, birkaç varlığa uygulanır ve yansıma aracılığıyla alınır.

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
- [Özel öznitelikler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
