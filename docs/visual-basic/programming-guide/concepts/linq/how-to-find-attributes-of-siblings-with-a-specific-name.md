---
title: 'Nasıl yapılır: (XPath-LINQ to XML) belirli bir ada sahip eşdüzeylerin özniteliklerini bulma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: 07fb5647950c450d08ab3235ac8cb396eff15305
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839060"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="0fb1e-102">Nasıl yapılır: (XPath-LINQ to XML) belirli bir ada sahip eşdüzeylerin özniteliklerini bulma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fb1e-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="0fb1e-103">Bu konuda, eşdüzey bağlam düğümünün tüm öznitelikleri bulmak amacıyla gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0fb1e-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="0fb1e-104">Yalnızca belirli bir ada sahip öznitelik koleksiyonu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0fb1e-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="0fb1e-105">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="0fb1e-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="0fb1e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0fb1e-106">Example</span></span>  
 <span data-ttu-id="0fb1e-107">Bu örnekte ilk bulur bir `Book` öğesi ve bulduğu tüm Eşdüzey öğeleri adlı `Book`ve ardından tüm öznitelikleri adlı bulur `id`.</span><span class="sxs-lookup"><span data-stu-id="0fb1e-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="0fb1e-108">Bir öznitelik koleksiyonu sonucudur.</span><span class="sxs-lookup"><span data-stu-id="0fb1e-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="0fb1e-109">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0fb1e-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books as XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>(0)  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XAttribute) = _  
    From el In book.Parent.<Book> _  
    Select el.Attribute("id")  
  
' XPath expression  
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _  
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()  
  
If list1.Count() = list2.Count() And _  
        (list1.Intersect(list2)).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XAttribute In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="0fb1e-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0fb1e-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fb1e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fb1e-111">See also</span></span>

- [<span data-ttu-id="0fb1e-112">LINQ to XML için XPath kullanıcıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fb1e-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
