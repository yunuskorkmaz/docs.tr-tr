---
title: 'Nasıl yapılır: Bul eşdüzey düğümleri (XPath-LINQ-XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: a448be9d86f9f2e2f85d45f9bc1f019b3f72305c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324167"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-c"></a><span data-ttu-id="6718e-102">Nasıl yapılır: Bul eşdüzey düğümleri (XPath-LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6718e-102">How to: Find Sibling Nodes (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="6718e-103">Belirli bir ada sahip bir düğümün tüm eşdüzey bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6718e-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="6718e-104">Bağlam düğümü de belirli ad varsa ortaya çıkan koleksiyonu bağlam düğümü içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6718e-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="6718e-105">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="6718e-105">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="6718e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="6718e-106">Example</span></span>  
 <span data-ttu-id="6718e-107">Bu örnek ilk bulur bir `Book` öğesi ve tüm kardeş öğeler adlı bulur `Book`.</span><span class="sxs-lookup"><span data-stu-id="6718e-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="6718e-108">Sonuçta elde edilen koleksiyon bağlam düğümü içerir.</span><span class="sxs-lookup"><span data-stu-id="6718e-108">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="6718e-109">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Books (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6718e-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="6718e-110">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="6718e-110">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6718e-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6718e-111">See Also</span></span>  
 [<span data-ttu-id="6718e-112">LINQ-XML XPath kullanıcıların (C#)</span><span class="sxs-lookup"><span data-stu-id="6718e-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
