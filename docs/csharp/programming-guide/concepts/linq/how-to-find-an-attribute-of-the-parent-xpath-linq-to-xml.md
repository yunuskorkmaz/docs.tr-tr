---
title: 'Nasıl yapılır: Bulma (XPath-LINQ to XML) üst özniteliği (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: e139e278141a8f42cddf8103f1c5d8d3195751e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668035"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="edb5d-102">Nasıl yapılır: Bulma (XPath-LINQ to XML) üst özniteliği (C#)</span><span class="sxs-lookup"><span data-stu-id="edb5d-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="edb5d-103">Bu konuda, üst öğeye gidin ve bir özniteliğin bulmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="edb5d-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="edb5d-104">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="edb5d-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="edb5d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="edb5d-105">Example</span></span>  
 <span data-ttu-id="edb5d-106">Bu örnekte ilk bulur bir `Author` öğesi.</span><span class="sxs-lookup"><span data-stu-id="edb5d-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="edb5d-107">Ardından bulduğu `id` üst öğesinin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="edb5d-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="edb5d-108">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="edb5d-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="edb5d-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="edb5d-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="edb5d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edb5d-110">See also</span></span>

- [<span data-ttu-id="edb5d-111">LINQ to XML için XPath kullanıcıları (C#)</span><span class="sxs-lookup"><span data-stu-id="edb5d-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
