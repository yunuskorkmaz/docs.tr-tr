---
title: Belirli bir özniteliğe sahip öğeleri bulma (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: e79cad3ad6fb0bf88e388b552f8e39327acfb4ad
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141043"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="2131e-102">Belirli bir özniteliğe sahip öğeleri bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2131e-102">How to find elements with a specific attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="2131e-103">Bazen belirli bir özniteliğe sahip olan tüm öğeleri bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2131e-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="2131e-104">Özniteliğin içeriğiyle ilgili endişeleriniz yok.</span><span class="sxs-lookup"><span data-stu-id="2131e-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="2131e-105">Bunun yerine, özniteliğinin varlığına göre ' ı seçmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="2131e-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="2131e-106">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="2131e-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="2131e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2131e-107">Example</span></span>  
 <span data-ttu-id="2131e-108">Aşağıdaki kod yalnızca `Select` özniteliği olan öğeleri seçer.</span><span class="sxs-lookup"><span data-stu-id="2131e-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
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
  
 <span data-ttu-id="2131e-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2131e-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  