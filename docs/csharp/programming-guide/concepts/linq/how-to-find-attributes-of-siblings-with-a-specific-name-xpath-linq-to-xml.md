---
title: Belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bulma (XPath-LINQ to XML) (C#)
description: Bağlam düğümünün eşdüzey öğelerinin tüm özniteliklerini bulmayı öğrenin. Örnek XML dosyası kullanan bir kod örneğini gözden geçirin.
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 12bba22c91fef92fc3383d028ff9dfb8bd3cfa3e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301703"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="dd5b5-104">Belirli bir ada sahip eşdüzey öğelerinin özniteliklerini bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="dd5b5-104">How to find attributes of siblings with a specific name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="dd5b5-105">Bu konu, bağlam düğümünün eşdüzey öğelerinin tüm özniteliklerinin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd5b5-105">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="dd5b5-106">Koleksiyonda yalnızca belirli bir ada sahip öznitelikler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="dd5b5-106">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="dd5b5-107">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="dd5b5-107">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="dd5b5-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd5b5-108">Example</span></span>  
 <span data-ttu-id="dd5b5-109">Bu örnek önce bir `Book` öğesi bulur, sonra adlı tüm eşdüzey öğeleri bulur ve `Book` sonra adlı tüm öznitelikleri bulur `id` .</span><span class="sxs-lookup"><span data-stu-id="dd5b5-109">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="dd5b5-110">Sonuç, özniteliklerin koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="dd5b5-110">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="dd5b5-111">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dd5b5-111">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="dd5b5-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="dd5b5-112">This example produces the following output:</span></span>  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  