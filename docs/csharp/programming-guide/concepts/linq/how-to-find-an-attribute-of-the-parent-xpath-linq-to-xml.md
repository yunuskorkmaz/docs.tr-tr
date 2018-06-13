---
title: 'Nasıl yapılır: bir öznitelik üst (XPath-LINQ-XML) bulunamadı (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 6f796bfb8f8b0051af4e31f6e82a503dbfbbc334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318805"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="11d0c-102">Nasıl yapılır: bir öznitelik üst (XPath-LINQ-XML) bulunamadı (C#)</span><span class="sxs-lookup"><span data-stu-id="11d0c-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="11d0c-103">Bu konuda, üst öğesine gidin ve bunu bir öznitelik bulunamadı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="11d0c-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="11d0c-104">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="11d0c-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="11d0c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="11d0c-105">Example</span></span>  
 <span data-ttu-id="11d0c-106">Bu örnek ilk bulur bir `Author` öğesi.</span><span class="sxs-lookup"><span data-stu-id="11d0c-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="11d0c-107">Ardından bulduğu `id` üst öğesinin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="11d0c-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="11d0c-108">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Books (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="11d0c-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement author =   
    books  
    .Root  
    .Element("Book")  
    .Element("Author");  
  
// LINQ to XML query  
XAttribute att1 =  
    author  
    .Parent  
    .Attribute("id");  
  
// XPath expression  
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();  
  
if (att1 == att2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(att1);  
```  
  
 <span data-ttu-id="11d0c-109">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="11d0c-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="11d0c-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11d0c-110">See Also</span></span>  
 [<span data-ttu-id="11d0c-111">LINQ-XML XPath kullanıcıların (C#)</span><span class="sxs-lookup"><span data-stu-id="11d0c-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
