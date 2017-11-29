---
title: "Nasıl yapılır: Filtre isteğe bağlı bir öğede (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc1b5384add88db209a71ec56dc1c5edf4caecb3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="5fe37-102">Nasıl yapılır: Filtre isteğe bağlı bir öğede (C#)</span><span class="sxs-lookup"><span data-stu-id="5fe37-102">How to: Filter on an Optional Element (C#)</span></span>
<span data-ttu-id="5fe37-103">Bazen, XML belgesinde var olmadığından emin değilseniz olsa bile bir öğe için filtre uygulamak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="5fe37-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="5fe37-104">Böylece belirli öğesinin alt öğesi sahip değilse, bir null başvuru özel durumu için filtre uygulayarak tetiklemez arama yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="5fe37-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="5fe37-105">Aşağıdaki örnekte, `Child5` öğesi yok bir `Type` alt öğesi, ancak sorgu hala yürütür doğru.</span><span class="sxs-lookup"><span data-stu-id="5fe37-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fe37-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fe37-106">Example</span></span>  
 <span data-ttu-id="5fe37-107">Bu örnekte <xref:System.Xml.Linq.Extensions.Elements%2A> genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5fe37-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="5fe37-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5fe37-108">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="5fe37-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fe37-109">Example</span></span>  
 <span data-ttu-id="5fe37-110">Aşağıdaki örnek bir ad alanı XML aynı sorgu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fe37-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="5fe37-111">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="5fe37-111">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="5fe37-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5fe37-112">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fe37-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fe37-113">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="5fe37-114">Temel sorgu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5fe37-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="5fe37-115">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="5fe37-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="5fe37-116">Projeksiyon işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="5fe37-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
