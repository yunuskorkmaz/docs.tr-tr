---
title: İsteğe bağlı bir öğeyi filtreleme (C#)
description: XML belgenizde var olduğundan emin olmasanız da, isteğe bağlı bir öğe için filtre uygulamayı öğrenin.
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: a1cd93b70ea2c077437b58bd341f51f15f014871
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302873"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="091e5-103">İsteğe bağlı bir öğeyi filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="091e5-103">How to filter on an optional element (C#)</span></span>
<span data-ttu-id="091e5-104">Bazen, XML belgenizde bulunduğundan emin olmasanız da bir öğeye filtre uygulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="091e5-104">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="091e5-105">Arama, belirli bir öğede alt öğe yoksa, filtre uygulayarak bir null başvuru özel durumu tetiklememesi için yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="091e5-105">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="091e5-106">Aşağıdaki örnekte, `Child5` öğesinin bir `Type` alt öğesi yoktur, ancak sorgu yine de doğru yürütülür.</span><span class="sxs-lookup"><span data-stu-id="091e5-106">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="091e5-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="091e5-107">Example</span></span>  
 <span data-ttu-id="091e5-108">Bu örnek, <xref:System.Xml.Linq.Extensions.Elements%2A> genişletme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="091e5-108">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="091e5-109">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="091e5-109">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="091e5-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="091e5-110">Example</span></span>  
 <span data-ttu-id="091e5-111">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="091e5-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="091e5-112">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="091e5-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="091e5-113">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="091e5-113">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="091e5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="091e5-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="091e5-115">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="091e5-115">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="091e5-116">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="091e5-116">Projection Operations (C#)</span></span>](./projection-operations.md)
