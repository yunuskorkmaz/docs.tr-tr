---
title: Belirli bir alt öğeye sahip bir öğe bulma (C#)
description: Belirli bir alt öğeye sahip olan bir öğeyi bulmayı öğrenin. Kod örneklerine ve ek kaynaklara bakın.
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 1d02f3d3af0a3711a5361941727e2e0b6c8bbdc9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301716"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="abf9c-104">Belirli bir alt öğeye sahip bir öğe bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="abf9c-104">How to find an element with a specific child element (C#)</span></span>
<span data-ttu-id="abf9c-105">Bu konu, belirli bir değere sahip bir alt öğesi olan belirli bir öğenin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="abf9c-105">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abf9c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="abf9c-106">Example</span></span>  
 <span data-ttu-id="abf9c-107">Örnek, `Test` `CommandLine` "Examp2.EXE" değerine sahip bir alt öğeye sahip öğeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="abf9c-107">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="abf9c-108">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: test yapılandırması (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="abf9c-108">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="abf9c-109">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="abf9c-109">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="abf9c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="abf9c-110">Example</span></span>  
 <span data-ttu-id="abf9c-111">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="abf9c-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="abf9c-112">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="abf9c-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="abf9c-113">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında test yapılandırması](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="abf9c-113">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="abf9c-114">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="abf9c-114">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="abf9c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abf9c-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="abf9c-116">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="abf9c-116">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="abf9c-117">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="abf9c-117">Projection Operations (C#)</span></span>](./projection-operations.md)
