---
title: 'Nasıl yapılır: (XPath-LINQ to XML) belirli bir ada sahip eşdüzeylerin özniteliklerini bulma (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 562f3a40e1670a76778a64570f980326d946a4c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584681"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="85ac5-102">Nasıl yapılır: (XPath-LINQ to XML) belirli bir ada sahip eşdüzeylerin özniteliklerini bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="85ac5-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="85ac5-103">Bu konuda, eşdüzey bağlam düğümünün tüm öznitelikleri bulmak amacıyla gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="85ac5-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="85ac5-104">Yalnızca belirli bir ada sahip öznitelik koleksiyonu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="85ac5-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="85ac5-105">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="85ac5-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="85ac5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="85ac5-106">Example</span></span>  
 <span data-ttu-id="85ac5-107">Bu örnekte ilk bulur bir `Book` öğesi ve bulduğu tüm Eşdüzey öğeleri adlı `Book`ve ardından tüm öznitelikleri adlı bulur `id`.</span><span class="sxs-lookup"><span data-stu-id="85ac5-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="85ac5-108">Bir öznitelik koleksiyonu sonucudur.</span><span class="sxs-lookup"><span data-stu-id="85ac5-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="85ac5-109">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="85ac5-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="85ac5-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="85ac5-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="85ac5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85ac5-111">See also</span></span>

- [<span data-ttu-id="85ac5-112">LINQ to XML için XPath kullanıcıları (C#)</span><span class="sxs-lookup"><span data-stu-id="85ac5-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
