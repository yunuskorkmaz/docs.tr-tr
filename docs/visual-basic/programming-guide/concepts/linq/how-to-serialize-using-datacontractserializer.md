---
title: 'Nasıl yapılır: DataContractSerializer (Visual Basic) kullanarak seri hale getirme'
ms.date: 07/20/2015
ms.assetid: ecaea518-8a0f-4249-b4e5-9b3fb0cdd8ad
ms.openlocfilehash: 9593dede3eb29aadc7ffb494e1d728cb8e679f0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826719"
---
# <a name="how-to-serialize-using-datacontractserializer-visual-basic"></a>Nasıl yapılır: DataContractSerializer (Visual Basic) kullanarak seri hale getirme
Bu konuda serileştirir ve kullanarak çıkarır bir örnek gösterilmektedir <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sayı içeren bir nesne oluşturur. <xref:System.Xml.Linq.XElement> nesneleri. Daha sonra bunları metin dosyalarına serileştirir ve bunları metin dosyalarından serisini kaldırır.  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Linq  
Imports System.IO  
Imports System.Runtime.Serialization  
  
Public Class XLinqTest  
    Shared Sub Main()  
        Test(Of XElement)(CreateXElement())  
        Test(Of XElementContainer)(New XElementContainer())  
        Test(Of XElementNullContainer)(New XElementNullContainer())  
    End Sub  
  
    Public Shared Sub Test(Of T)(ByRef obj)  
        Dim s As DataContractSerializer = New DataContractSerializer(GetType(T))  
        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Create)  
            Console.WriteLine("Testing for type: {0}", GetType(T))  
            s.WriteObject(fs, obj)  
        End Using  
  
        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Open)  
            Dim s2 As Object = s.ReadObject(fs)  
            If s2 Is Nothing Then  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)")  
            Else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType())  
            End If  
        End Using  
    End Sub  
  
    Public Shared Function CreateXElement() As XElement  
        Return New XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"))  
    End Function  
End Class  
  
<DataContract()> _  
Public Class XElementContainer  
    <DataMember()> _  
    Public member As XElement  
  
    Public Sub XElementContainer()  
        member = XLinqTest.CreateXElement()  
    End Sub  
End Class  
  
<DataContract()> _  
Public Class XElementNullContainer  
    <DataMember()> _  
    Public member As XElement  
  
    Public Sub XElementNullContainer()  
        member = Nothing  
    End Sub  
End Class  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [(Visual Basic) XElement nesneleri içeren nesne grafiklerini serileştirme](../../../../visual-basic/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)
