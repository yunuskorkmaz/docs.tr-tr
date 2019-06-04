---
title: 'Nasıl yapılır: İsteğe bağlı öğeyi filtreleme (C#)'
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 6dba732268ff9ff1a206cd13e31f94c394a17b39
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485712"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="40eb4-102">Nasıl yapılır: İsteğe bağlı öğeyi filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="40eb4-102">How to: Filter on an Optional Element (C#)</span></span>
<span data-ttu-id="40eb4-103">Bazen, XML belgesinde varolduğundan emin olmadığınız halde bir öğe için filtrelemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="40eb4-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="40eb4-104">Arama, böylece belirli bir öğenin alt öğesi yoksa, bir null başvurusu özel durumu için filtreleyerek tetiklemez yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="40eb4-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="40eb4-105">Aşağıdaki örnekte, `Child5` öğesi yok bir `Type` alt öğesi, ancak sorgu hala yürütür doğru.</span><span class="sxs-lookup"><span data-stu-id="40eb4-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40eb4-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="40eb4-106">Example</span></span>  
 <span data-ttu-id="40eb4-107">Bu örnekte <xref:System.Xml.Linq.Extensions.Elements%2A> genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="40eb4-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="40eb4-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="40eb4-108">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="40eb4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="40eb4-109">Example</span></span>  
 <span data-ttu-id="40eb4-110">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="40eb4-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="40eb4-111">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="40eb4-111">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="40eb4-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="40eb4-112">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="40eb4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40eb4-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="40eb4-114">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="40eb4-114">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="40eb4-115">Projeksiyon işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="40eb4-115">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
