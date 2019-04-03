---
title: 'Nasıl yapılır: Bir (XPath-LINQ to XML) üst öğenin özniteliğini bulma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: ded20c173063492d260aee5ba55f3c4c585bd961
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828660"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="4dcf0-102">Nasıl yapılır: Bir (XPath-LINQ to XML) üst öğenin özniteliğini bulma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dcf0-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="4dcf0-103">Bu konuda, üst öğeye gidin ve bir özniteliğin bulmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4dcf0-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="4dcf0-104">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="4dcf0-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="4dcf0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4dcf0-105">Example</span></span>  
 <span data-ttu-id="4dcf0-106">Bu örnekte ilk bulur bir `Author` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4dcf0-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="4dcf0-107">Ardından bulduğu `id` üst öğesinin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4dcf0-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="4dcf0-108">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4dcf0-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="4dcf0-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4dcf0-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="4dcf0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dcf0-110">See also</span></span>

- [<span data-ttu-id="4dcf0-111">LINQ to XML için XPath kullanıcıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dcf0-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
