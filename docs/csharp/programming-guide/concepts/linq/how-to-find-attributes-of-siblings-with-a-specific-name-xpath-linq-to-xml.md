---
title: 'Nasıl yapılır: Belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bul (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 78795f164490dddd6bdc8dae04961c028228ab0c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593521"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="4d4d9-102">Nasıl yapılır: Belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bul (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4d4d9-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="4d4d9-103">Bu konu, bağlam düğümünün eşdüzey öğelerinin tüm özniteliklerinin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="4d4d9-104">Koleksiyonda yalnızca belirli bir ada sahip öznitelikler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="4d4d9-105">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="4d4d9-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="4d4d9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d4d9-106">Example</span></span>  
 <span data-ttu-id="4d4d9-107">Bu örnek önce bir `Book` öğesi bulur, sonra adlı `Book`tüm eşdüzey öğeleri bulur ve sonra adlı `id`tüm öznitelikleri bulur.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="4d4d9-108">Sonuç, özniteliklerin koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="4d4d9-109">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4d4d9-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="4d4d9-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4d4d9-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  