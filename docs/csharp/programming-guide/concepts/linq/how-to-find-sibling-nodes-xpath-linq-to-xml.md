---
title: Kardeş düğümleri bulma (XPath-LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: c201dcea5e6d148ae0998eb27d4e42df5b15309f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169213"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="19227-102">Kardeş düğümleri bulma (XPath-LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="19227-102">How to find sibling nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="19227-103">Belirli bir ada sahip bir düğümün tüm kardeşlerini bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19227-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="19227-104">Bağlam düğümü de belirli bir ada sahipse, ortaya çıkan koleksiyon bağlam düğümü içerebilir.</span><span class="sxs-lookup"><span data-stu-id="19227-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="19227-105">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="19227-105">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="19227-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="19227-106">Example</span></span>  
 <span data-ttu-id="19227-107">Bu örnekte `Book` önce bir öğe bulur ve `Book`sonra adı geçen tüm kardeş öğeleri bulur.</span><span class="sxs-lookup"><span data-stu-id="19227-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="19227-108">Ortaya çıkan koleksiyon bağlam düğümiçerir.</span><span class="sxs-lookup"><span data-stu-id="19227-108">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="19227-109">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Kitaplar (LINQ-XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="19227-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =
    books  
    .Root  
    .Elements("Book")  
    .Skip(1)  
    .First();  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    book  
    .Parent  
    .Elements("Book");  
  
// XPath expression  
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="19227-110">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="19227-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Book id="bk101">  
  <Author>Garghentini, Davide</Author>  
  <Title>XML Developer's Guide</Title>  
  <Genre>Computer</Genre>  
  <Price>44.95</Price>  
  <PublishDate>2000-10-01</PublishDate>  
  <Description>An in-depth look at creating applications
      with XML.</Description>  
</Book>  
<Book id="bk102">  
  <Author>Garcia, Debra</Author>  
  <Title>Midnight Rain</Title>  
  <Genre>Fantasy</Genre>  
  <Price>5.95</Price>  
  <PublishDate>2000-12-16</PublishDate>  
  <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>  
</Book>  
```  
