---
title: Hemen önceki kardeş (XPath-LINQ - XML) (C#) nasıl bulabilirim?
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 1e5aece41021642d43b7f6f7b78bb105156ee4ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141008"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="fd1b3-102">Hemen önceki kardeş (XPath-LINQ - XML) (C#) nasıl bulabilirim?</span><span class="sxs-lookup"><span data-stu-id="fd1b3-102">How to find the immediate preceding sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="fd1b3-103">Bazen bir düğüm için hemen önceki kardeş bulmak istiyorum.</span><span class="sxs-lookup"><span data-stu-id="fd1b3-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="fd1b3-104">XPath'te önceki kardeş eksenler için konumsal yüklemlerin semantikindeki farktan [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]dolayı, bu daha ilginç karşılaştırmalardan biridir.</span><span class="sxs-lookup"><span data-stu-id="fd1b3-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd1b3-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd1b3-105">Example</span></span>  
 <span data-ttu-id="fd1b3-106">Bu örnekte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu <xref:System.Linq.Enumerable.Last%2A> tarafından <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>döndürülen koleksiyondaki son düğümü bulmak için işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd1b3-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="fd1b3-107">Bunun aksine, XPath ifadesi hemen önceki öğeyi bulmak için 1 değeri olan bir yüklem kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd1b3-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
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
  
 <span data-ttu-id="fd1b3-108">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fd1b3-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Child3 />  
```  
