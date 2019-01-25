---
title: 'Nasıl yapılır: Önceki eşdüzeyi (XPath-LINQ to XML) bulunamadı (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: 81113c30cae0eb29fe0cf4b783fb031156353130
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572480"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="27bfc-102">Nasıl yapılır: Önceki eşdüzeyi (XPath-LINQ to XML) bulunamadı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27bfc-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="27bfc-103">Bazen bir düğüme önceki eşdüzeyi bulma istersiniz.</span><span class="sxs-lookup"><span data-stu-id="27bfc-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="27bfc-104">XPath başlangıcı yerine sonundan önceki eşdüzey eksenleri için konumsal doğrulamaları semantiği fark nedeniyle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu daha ilgi çekici karşılaştırmalar biridir.</span><span class="sxs-lookup"><span data-stu-id="27bfc-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27bfc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="27bfc-105">Example</span></span>  
 <span data-ttu-id="27bfc-106">Bu örnekte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu kullandığı <xref:System.Linq.Enumerable.Last%2A> son düğümü tarafından döndürülen bir koleksiyonda bulunacak işleci <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="27bfc-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="27bfc-107">Aksine, XPath ifadesi hemen önceki öğeyi bulmak için 1 değerini bir koşul kullanır.</span><span class="sxs-lookup"><span data-stu-id="27bfc-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
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
  
 <span data-ttu-id="27bfc-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="27bfc-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="27bfc-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27bfc-109">See also</span></span>
- [<span data-ttu-id="27bfc-110">LINQ to XML için XPath kullanıcıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27bfc-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
