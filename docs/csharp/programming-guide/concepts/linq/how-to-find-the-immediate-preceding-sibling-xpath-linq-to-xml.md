---
title: 'Nasıl yapılır: hemen önceki eşdüzey (XPath-LINQ-XML) Bul (C#)'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 82c0ee6e7340ada18fb2077c0b8b04fb6a41671a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318561"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="aada7-102">Nasıl yapılır: hemen önceki eşdüzey (XPath-LINQ-XML) Bul (C#)</span><span class="sxs-lookup"><span data-stu-id="aada7-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="aada7-103">Bazen bir düğüme hemen önceki eşdüzey bulmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="aada7-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="aada7-104">XPath tersine önceki eşdüzey eksenlerin konumsal koşulları semantiği fark nedeniyle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu daha ilginç karşılaştırmaları biridir.</span><span class="sxs-lookup"><span data-stu-id="aada7-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aada7-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="aada7-105">Example</span></span>  
 <span data-ttu-id="aada7-106">Bu örnekte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu kullanır <xref:System.Linq.Enumerable.Last%2A> tarafından döndürülen bir koleksiyondaki son düğümünü bulmayı işleci <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="aada7-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="aada7-107">Bunun aksine, XPath ifadesi hemen önceki öğeyi bulmak için 1 değerine sahip bir koşul kullanır.</span><span class="sxs-lookup"><span data-stu-id="aada7-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="aada7-108">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="aada7-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="aada7-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aada7-109">See Also</span></span>  
 [<span data-ttu-id="aada7-110">LINQ-XML XPath kullanıcıların (C#)</span><span class="sxs-lookup"><span data-stu-id="aada7-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
