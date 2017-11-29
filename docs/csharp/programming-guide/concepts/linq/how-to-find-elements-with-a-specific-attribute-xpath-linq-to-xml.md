---
title: "Nasıl yapılır: Bul (XPath-LINQ-XML) belirli bir özniteliği olan öğeleri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66053135dbfdf6f61ff1f09b846acd9d9cfe054f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="9b263-102">Nasıl yapılır: Bul (XPath-LINQ-XML) belirli bir özniteliği olan öğeleri (C#)</span><span class="sxs-lookup"><span data-stu-id="9b263-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="9b263-103">Bazen belirli bir özniteliği olan tüm öğeleri bulmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="9b263-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="9b263-104">Öznitelik içeriği hakkında ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="9b263-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="9b263-105">Bunun yerine, seçmek öznitelik varlığını temel istiyor.</span><span class="sxs-lookup"><span data-stu-id="9b263-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="9b263-106">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="9b263-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="9b263-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b263-107">Example</span></span>  
 <span data-ttu-id="9b263-108">Aşağıdaki kod olan öğeleri seçer `Select` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9b263-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
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
  
 <span data-ttu-id="9b263-109">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="9b263-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b263-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b263-110">See Also</span></span>  
 [<span data-ttu-id="9b263-111">LINQ-XML XPath kullanıcıların (C#)</span><span class="sxs-lookup"><span data-stu-id="9b263-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
