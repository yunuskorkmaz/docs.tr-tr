---
title: "Nasıl yapılır: DataContractSerializer (Visual Basic) kullanarak serileştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecaea518-8a0f-4249-b4e5-9b3fb0cdd8ad
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e86409b3b1ff499a3be789e1a22947dff6011517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-serialize-using-datacontractserializer-visual-basic"></a><span data-ttu-id="66a6d-102">Nasıl yapılır: DataContractSerializer (Visual Basic) kullanarak serileştirme</span><span class="sxs-lookup"><span data-stu-id="66a6d-102">How to: Serialize Using DataContractSerializer (Visual Basic)</span></span>
<span data-ttu-id="66a6d-103">Bu konuda, serileştirir ve kullanılarak seri durumdan çıkarır bir örnek gösterilmektedir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="66a6d-103">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66a6d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="66a6d-104">Example</span></span>  
 <span data-ttu-id="66a6d-105">Aşağıdaki örnek, bir dizi içeren nesneleri oluşturur <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="66a6d-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="66a6d-106">Bunları metin dosyalarına serileştirir ve bunları metin dosyalarından çıkarır.</span><span class="sxs-lookup"><span data-stu-id="66a6d-106">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
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
  
 <span data-ttu-id="66a6d-107">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="66a6d-107">This example produces the following output:</span></span>  
  
```  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
  
## <a name="see-also"></a><span data-ttu-id="66a6d-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66a6d-108">See Also</span></span>  
 [<span data-ttu-id="66a6d-109">XElement nesneler (Visual Basic) içeren nesne grafiklerinin seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="66a6d-109">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)
