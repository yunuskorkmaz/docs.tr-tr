---
title: 'Nasıl yapılır: Hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: bc0a3250cf1f56ebf9a367f6472be8f3230cee5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253626"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="c6422-102">Nasıl yapılır: Hemen önceki eşdüzey öğeyi bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c6422-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="c6422-103">Bazen bir düğüme hemen önceki eşdüzey öğeyi bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6422-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="c6422-104">XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]'teki önceki eşdüzey eksenlerine yönelik konumsal koşulların semantiğinin farkı nedeniyle bu, daha ilginç karşılaştırmalardan biridir.</span><span class="sxs-lookup"><span data-stu-id="c6422-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6422-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6422-105">Example</span></span>  
 <span data-ttu-id="c6422-106">Bu örnekte [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu, tarafından <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>döndürülen koleksiyondaki son <xref:System.Linq.Enumerable.Last%2A> düğümü bulmak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6422-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="c6422-107">Buna karşılık, XPath ifadesi hemen önceki öğeyi bulmak için değeri 1 olan bir koşul kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6422-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
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
  
 <span data-ttu-id="c6422-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c6422-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Child3 />  
```  
