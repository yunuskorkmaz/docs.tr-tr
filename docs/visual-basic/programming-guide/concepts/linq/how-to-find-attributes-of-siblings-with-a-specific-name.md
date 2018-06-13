---
title: 'Nasıl yapılır: belirli bir ada (XPath-LINQ-XML) ile eş özniteliklerini Bul (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: 467a9a5f529111b45fccda79437ccc6538f1372a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643615"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="5d434-102">Nasıl yapılır: belirli bir ada (XPath-LINQ-XML) ile eş özniteliklerini Bul (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d434-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="5d434-103">Bu konu, bağlam düğümünün eşdüzeyi tüm özniteliklerini bulmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5d434-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="5d434-104">Yalnızca belirli bir ada sahip öznitelik koleksiyonu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5d434-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="5d434-105">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="5d434-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="5d434-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d434-106">Example</span></span>  
 <span data-ttu-id="5d434-107">Bu örnek ilk bulur bir `Book` öğesi ve tüm kardeş öğeler adlı bulur `Book`ve ardından tüm öznitelikleri adlı bulur `id`.</span><span class="sxs-lookup"><span data-stu-id="5d434-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="5d434-108">Sonuç öznitelikleri koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="5d434-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="5d434-109">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Books (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5d434-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="5d434-110">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="5d434-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d434-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d434-111">See Also</span></span>  
 [<span data-ttu-id="5d434-112">LINQ-XML XPath kullanıcıların (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d434-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
