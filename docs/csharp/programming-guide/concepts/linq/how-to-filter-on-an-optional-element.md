---
title: 'Nasıl yapılır: Isteğe bağlı bir öğe (C#) üzerinde filtrele'
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 0f8e17d99085ad04ed76b83bce806418ca6d60cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253829"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="34b54-102">Nasıl yapılır: Isteğe bağlı bir öğe (C#) üzerinde filtrele</span><span class="sxs-lookup"><span data-stu-id="34b54-102">How to: Filter on an Optional Element (C#)</span></span>
<span data-ttu-id="34b54-103">Bazen, XML belgenizde bulunduğundan emin olmasanız da bir öğeye filtre uygulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34b54-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="34b54-104">Arama, belirli bir öğede alt öğe yoksa, filtre uygulayarak bir null başvuru özel durumu tetiklememesi için yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="34b54-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="34b54-105">Aşağıdaki örnekte, `Child5` öğesinin bir `Type` alt öğesi yoktur, ancak sorgu yine de doğru yürütülür.</span><span class="sxs-lookup"><span data-stu-id="34b54-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34b54-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="34b54-106">Example</span></span>  
 <span data-ttu-id="34b54-107">Bu örnek, <xref:System.Xml.Linq.Extensions.Elements%2A> genişletme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="34b54-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="34b54-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="34b54-108">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="34b54-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="34b54-109">Example</span></span>  
 <span data-ttu-id="34b54-110">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="34b54-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="34b54-111">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="34b54-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="34b54-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="34b54-112">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="34b54-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34b54-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="34b54-114">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="34b54-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="34b54-115">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="34b54-115">Projection Operations (C#)</span></span>](./projection-operations.md)
