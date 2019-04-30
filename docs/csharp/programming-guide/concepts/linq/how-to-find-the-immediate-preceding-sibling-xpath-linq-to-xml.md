---
title: 'Nasıl yapılır: Önceki eşdüzeyi (XPath-LINQ to XML) bulun (C#)'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 00b74edd67df65522f9f95e7f48c66a9e17a937c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702223"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="960e1-102">Nasıl yapılır: Önceki eşdüzeyi (XPath-LINQ to XML) bulun (C#)</span><span class="sxs-lookup"><span data-stu-id="960e1-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="960e1-103">Bazen bir düğüme önceki eşdüzeyi bulma istersiniz.</span><span class="sxs-lookup"><span data-stu-id="960e1-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="960e1-104">XPath başlangıcı yerine sonundan önceki eşdüzey eksenleri için konumsal doğrulamaları semantiği fark nedeniyle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu daha ilgi çekici karşılaştırmalar biridir.</span><span class="sxs-lookup"><span data-stu-id="960e1-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="960e1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="960e1-105">Example</span></span>  
 <span data-ttu-id="960e1-106">Bu örnekte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu kullandığı <xref:System.Linq.Enumerable.Last%2A> son düğümü tarafından döndürülen bir koleksiyonda bulunacak işleci <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="960e1-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="960e1-107">Aksine, XPath ifadesi hemen önceki öğeyi bulmak için 1 değerini bir koşul kullanır.</span><span class="sxs-lookup"><span data-stu-id="960e1-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
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
  
 <span data-ttu-id="960e1-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="960e1-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="960e1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="960e1-109">See also</span></span>

- [<span data-ttu-id="960e1-110">LINQ to XML için XPath kullanıcıları (C#)</span><span class="sxs-lookup"><span data-stu-id="960e1-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
