---
title: İsteğe bağlı bir öğeye nasıl filtre yapılır (C#)
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: c9f844619cbb3d7a66ca66989baa900e0fd7bc2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141246"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="cd6ad-102">İsteğe bağlı bir öğeye nasıl filtre yapılır (C#)</span><span class="sxs-lookup"><span data-stu-id="cd6ad-102">How to filter on an optional element (C#)</span></span>
<span data-ttu-id="cd6ad-103">Bazen XML belgenizde var olduğundan emin değilseniz bile bir öğe için filtre yapmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="cd6ad-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="cd6ad-104">Arama, belirli öğealt öğeye sahip değilse, bunun için filtre uygulayarak null bir başvuru özel durum tetiklemez, böylece yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="cd6ad-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="cd6ad-105">Aşağıdaki örnekte, `Child5` öğenin bir `Type` alt öğesi yoktur, ancak sorgu yine de doğru yürütülür.</span><span class="sxs-lookup"><span data-stu-id="cd6ad-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd6ad-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd6ad-106">Example</span></span>  
 <span data-ttu-id="cd6ad-107">Bu örnek, <xref:System.Xml.Linq.Extensions.Elements%2A> uzantı yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd6ad-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="cd6ad-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cd6ad-108">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="cd6ad-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd6ad-109">Example</span></span>  
 <span data-ttu-id="cd6ad-110">Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd6ad-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cd6ad-111">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd6ad-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="cd6ad-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cd6ad-112">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd6ad-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd6ad-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cd6ad-114">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="cd6ad-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="cd6ad-115">Projeksiyon İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="cd6ad-115">Projection Operations (C#)</span></span>](./projection-operations.md)
