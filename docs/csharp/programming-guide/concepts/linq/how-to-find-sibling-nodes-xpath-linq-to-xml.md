---
title: 'Nasıl yapılır: eşdüzey düğümleri (XPath-LINQ to XML) bulma (C#)'
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: e10b23c311e4e7debf228c01c898f3582e2ac8d4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865364"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="5c959-102">Nasıl yapılır: eşdüzey düğümleri (XPath-LINQ to XML) bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="5c959-102">How to: Find Sibling Nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="5c959-103">Belirli bir ada sahip tüm bir düğümün eşdüzey bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c959-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="5c959-104">Bağlam düğümünün belirli bir ada sahipse, sonuçta elde edilen koleksiyon bağlam düğümünün içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5c959-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="5c959-105">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="5c959-105">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="5c959-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c959-106">Example</span></span>  
 <span data-ttu-id="5c959-107">Bu örnekte ilk bulur bir `Book` öğesi ve bulduğu tüm Eşdüzey öğeleri adlı `Book`.</span><span class="sxs-lookup"><span data-stu-id="5c959-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="5c959-108">Sonuçta elde edilen koleksiyon bağlam düğümü içerir.</span><span class="sxs-lookup"><span data-stu-id="5c959-108">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="5c959-109">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: kitaplar (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5c959-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="5c959-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5c959-110">This example produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="5c959-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c959-111">See Also</span></span>

- [<span data-ttu-id="5c959-112">LINQ to XML için XPath kullanıcıları (C#)</span><span class="sxs-lookup"><span data-stu-id="5c959-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
