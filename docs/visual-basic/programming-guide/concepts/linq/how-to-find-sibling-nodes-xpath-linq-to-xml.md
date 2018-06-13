---
title: 'Nasıl yapılır: Bul eşdüzey düğümleri (XPath-LINQ-XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 73082738-2113-4438-8545-98d5df0927cb
ms.openlocfilehash: ded92d8cb7cb2d2aa6c6342c3ddec347e25ff79a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642888"
---
# <a name="how-to-find-sibling-nodes-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="7e0a3-102">Nasıl yapılır: Bul eşdüzey düğümleri (XPath-LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e0a3-102">How to: Find Sibling Nodes (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="7e0a3-103">Belirli bir ada sahip bir düğümün tüm eşdüzey bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e0a3-103">You might want to find all siblings of a node that have a specific name.</span></span> <span data-ttu-id="7e0a3-104">Bağlam düğümü de belirli ad varsa ortaya çıkan koleksiyonu bağlam düğümü içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7e0a3-104">The resulting collection might include the context node if the context node also has the specific name.</span></span>  
  
 <span data-ttu-id="7e0a3-105">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="7e0a3-105">The XPath expression is:</span></span>  
  
 `../Book`  
  
## <a name="example"></a><span data-ttu-id="7e0a3-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e0a3-106">Example</span></span>  
 <span data-ttu-id="7e0a3-107">Bu örnek ilk bulur bir `Book` öğesi ve tüm kardeş öğeler adlı bulur `Book`.</span><span class="sxs-lookup"><span data-stu-id="7e0a3-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`.</span></span> <span data-ttu-id="7e0a3-108">Sonuçta elde edilen koleksiyon bağlam düğümü içerir.</span><span class="sxs-lookup"><span data-stu-id="7e0a3-108">The resulting collection includes the context node.</span></span>  
  
 <span data-ttu-id="7e0a3-109">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Books (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7e0a3-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>.Skip(1).First()  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = book.Parent.<Book>  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = book.XPathSelectElements("../Book")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="7e0a3-110">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="7e0a3-110">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e0a3-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e0a3-111">See Also</span></span>  
 [<span data-ttu-id="7e0a3-112">LINQ-XML XPath kullanıcıların (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e0a3-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
