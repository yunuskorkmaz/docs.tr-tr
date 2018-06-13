---
title: 'Nasıl yapılır: belirli bir ada (XPath-LINQ-XML) ile eş özniteliklerini Bul (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 0e87208e033c4960843a82c9abd2b4ebd4f74d3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315873"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="664ea-102">Nasıl yapılır: belirli bir ada (XPath-LINQ-XML) ile eş özniteliklerini Bul (C#)</span><span class="sxs-lookup"><span data-stu-id="664ea-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="664ea-103">Bu konu, bağlam düğümünün eşdüzeyi tüm özniteliklerini bulmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="664ea-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="664ea-104">Yalnızca belirli bir ada sahip öznitelik koleksiyonu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="664ea-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="664ea-105">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="664ea-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="664ea-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="664ea-106">Example</span></span>  
 <span data-ttu-id="664ea-107">Bu örnek ilk bulur bir `Book` öğesi ve tüm kardeş öğeler adlı bulur `Book`ve ardından tüm öznitelikleri adlı bulur `id`.</span><span class="sxs-lookup"><span data-stu-id="664ea-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="664ea-108">Sonuç öznitelikleri koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="664ea-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="664ea-109">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Books (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="664ea-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="664ea-110">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="664ea-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="664ea-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="664ea-111">See Also</span></span>  
 [<span data-ttu-id="664ea-112">LINQ-XML XPath kullanıcıların (C#)</span><span class="sxs-lookup"><span data-stu-id="664ea-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
