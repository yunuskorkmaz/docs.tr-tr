---
title: Belirli bir alt öğe (C#) ile bir öğeyi bulma
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 0536b1b92d4d7fc18b5d406bbcd24aefc6a840c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141152"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="ce2b1-102">Belirli bir alt öğe (C#) ile bir öğeyi bulma</span><span class="sxs-lookup"><span data-stu-id="ce2b1-102">How to find an element with a specific child element (C#)</span></span>
<span data-ttu-id="ce2b1-103">Bu konu, belirli bir değere sahip bir alt öğeye sahip belirli bir öğeyi nasıl bulabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce2b1-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce2b1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce2b1-104">Example</span></span>  
 <span data-ttu-id="ce2b1-105">Örnek, "Examp2.EXE" değerine sahip bir `Test` `CommandLine` alt öğeye sahip öğeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="ce2b1-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="ce2b1-106">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Test Yapılandırması (LINQ -XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ce2b1-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="ce2b1-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ce2b1-107">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="ce2b1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce2b1-108">Example</span></span>  
 <span data-ttu-id="ce2b1-109">Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce2b1-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ce2b1-110">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ce2b1-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ce2b1-111">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında Test Yapılandırması.](./sample-xml-file-test-configuration-in-a-namespace1.md)</span><span class="sxs-lookup"><span data-stu-id="ce2b1-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="ce2b1-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ce2b1-112">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce2b1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce2b1-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="ce2b1-114">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="ce2b1-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ce2b1-115">Projeksiyon İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="ce2b1-115">Projection Operations (C#)</span></span>](./projection-operations.md)
