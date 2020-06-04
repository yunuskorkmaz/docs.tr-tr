---
title: 'Nasıl yapılır: Üst Öğenin Özniteliğini Bulma (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: 98b6e0e55390a2be13968e455321311661d81e84
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405306"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="3624c-102">Nasıl yapılır: üst öğenin bir özniteliğini bulma (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3624c-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3624c-103">Bu konu başlığı altında, üst öğeye gitme ve bir özniteliği bulma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3624c-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="3624c-104">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="3624c-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="3624c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3624c-105">Example</span></span>  
 <span data-ttu-id="3624c-106">Bu örnek önce bir `Author` öğesi bulur.</span><span class="sxs-lookup"><span data-stu-id="3624c-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="3624c-107">Daha sonra `id` üst öğenin özniteliğini bulur.</span><span class="sxs-lookup"><span data-stu-id="3624c-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="3624c-108">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3624c-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()  
  
' LINQ to XML query  
Dim att1 As XAttribute = author.Parent.Attribute("id")  
  
' XPath expression  
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _  
    IEnumerable).Cast(Of XAttribute)().First()  
  
If att1 Is att2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(att1)  
```  
  
 <span data-ttu-id="3624c-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3624c-109">This example produces the following output:</span></span>  
  
```console  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="3624c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3624c-110">See also</span></span>

- [<span data-ttu-id="3624c-111">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3624c-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
