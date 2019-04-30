---
title: 'Nasıl yapılır: (XPath-LINQ to XML) belirli bir özniteliğe sahip öğeleri bulma (C#)'
ms.date: 07/20/2015
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: c5b8ae9a41c5b05438d14f2717c8edfb151d47c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701989"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="8e4db-102">Nasıl yapılır: (XPath-LINQ to XML) belirli bir özniteliğe sahip öğeleri bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="8e4db-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="8e4db-103">Bazen belirli bir özniteliği olan tüm öğeleri bulmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="8e4db-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="8e4db-104">Özniteliğin içeriği hakkında endişe değildir.</span><span class="sxs-lookup"><span data-stu-id="8e4db-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="8e4db-105">Bunun yerine, seçilecek öznitelik varlığı üzerinde temel istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="8e4db-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="8e4db-106">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="8e4db-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="8e4db-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e4db-107">Example</span></span>  
 <span data-ttu-id="8e4db-108">Aşağıdaki kodu olan öğeleri seçer `Select` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8e4db-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(  
@"<Root>  
    <Child1>1</Child1>  
    <Child2 Select='true'>2</Child2>  
    <Child3>3</Child3>  
    <Child4 Select='true'>4</Child4>  
    <Child5>5</Child5>  
</Root>");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in doc.Elements()  
    where el.Attribute("Select") != null  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 =  
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="8e4db-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8e4db-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e4db-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e4db-110">See also</span></span>

- [<span data-ttu-id="8e4db-111">LINQ to XML için XPath kullanıcıları (C#)</span><span class="sxs-lookup"><span data-stu-id="8e4db-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
