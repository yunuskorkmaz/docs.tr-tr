---
title: "Nasıl yapılır: Basit değeri, bir öğenin (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 673b890ab842d1c18c8020eefe03d90086d1bf4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="5a1be-102">Nasıl yapılır: Basit değeri, bir öğenin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a1be-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>
<span data-ttu-id="5a1be-103">Bu konuda, basit bir öğe değerini almak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5a1be-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="5a1be-104">Basit yalnızca belirli öğesinin değeri tek bir dize halinde birleştirilmiş tüm alt öğelerinin değerlerini içerir derin değeri aksine değerdir.</span><span class="sxs-lookup"><span data-stu-id="5a1be-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="5a1be-105">Her iki çevrim kullanarak bir öğe değerini aldığınızda veya <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği, derin değeri alacak.</span><span class="sxs-lookup"><span data-stu-id="5a1be-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="5a1be-106">Basit değerini almak için kullanabileceğiniz `ShallowValue` genişletme yöntemi, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5a1be-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the follwing example.</span></span> <span data-ttu-id="5a1be-107">Basit değeri alınırken içeriğine göre öğelerini seçmek istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5a1be-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="5a1be-108">Aşağıdaki örnekte basit bir öğenin değerini alır. bir genişletme yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="5a1be-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="5a1be-109">Ardından, hesaplanan değeri içeren tüm öğeler listelemek için genişletme yöntemi sorguda kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a1be-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a1be-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a1be-110">Example</span></span>  
 <span data-ttu-id="5a1be-111">Aşağıdaki metin dosyası Report.xml, bu örnek kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="5a1be-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```vb  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function ShallowValue(ByVal xe As XElement)  
        Return xe _  
               .Nodes() _  
               .OfType(Of XText)() _  
               .Aggregate(New StringBuilder(), _  
                              Function(s, c) s.Append(c), _  
                              Function(s) s.ToString())  
    End Function  
  
    Sub Main()  
        Dim root As XElement = XElement.Load("Report.xml")  
  
        Dim query As IEnumerable(Of XElement) = _  
            From el In root.Descendants() _  
            Where (el.ShallowValue().StartsWith("=")) _  
            Select el  
  
        For Each q As XElement In query  
            Console.WriteLine("{0}{1}{2}", _  
                q.Name.ToString().PadRight(8), _  
                q.Attribute("Name").ToString().PadRight(20), _  
                q.ShallowValue())  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="5a1be-112">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="5a1be-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a1be-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a1be-113">See Also</span></span>  
 [<span data-ttu-id="5a1be-114">LINQ-XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a1be-114">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
