---
title: 'Nasıl yapılır: hemen önceki eşdüzey (XPath-LINQ-XML) bulunamadı (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 47ba557343d0f691c2ee0f2c56102df313ecfb30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641121"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="bbf30-102">Nasıl yapılır: hemen önceki eşdüzey (XPath-LINQ-XML) bulunamadı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbf30-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bbf30-103">Bazen bir düğüme hemen önceki eşdüzey bulmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="bbf30-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="bbf30-104">XPath tersine önceki eşdüzey eksenlerin konumsal koşulları semantiği fark nedeniyle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu daha ilginç karşılaştırmaları biridir.</span><span class="sxs-lookup"><span data-stu-id="bbf30-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf30-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbf30-105">Example</span></span>  
 <span data-ttu-id="bbf30-106">Bu örnekte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu kullanır <xref:System.Linq.Enumerable.Last%2A> tarafından döndürülen bir koleksiyondaki son düğümünü bulmayı işleci <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbf30-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="bbf30-107">Bunun aksine, XPath ifadesi hemen önceki öğeyi bulmak için 1 değerine sahip bir koşul kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbf30-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1/>  
        <Child2/>  
        <Child3/>  
        <Child4/>  
    </Root>  
Dim child4 As XElement = root.Element("Child4")  
  
' LINQ to XML query  
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()  
  
' XPath expression  
Dim el2 As XElement = _  
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _  
    IEnumerable).Cast(Of XElement)().First()  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 <span data-ttu-id="bbf30-108">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="bbf30-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbf30-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbf30-109">See Also</span></span>  
 [<span data-ttu-id="bbf30-110">LINQ-XML XPath kullanıcıların (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbf30-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
