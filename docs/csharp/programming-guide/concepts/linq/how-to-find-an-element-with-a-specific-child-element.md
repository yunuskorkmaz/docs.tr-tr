---
title: "Nasıl yapılır: belirli alt öğesi (C#) olan bir öğe bulunamadı"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d4d865b6e412f6f039df3578340db046ca59fa6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="e7f04-102">Nasıl yapılır: belirli alt öğesi (C#) olan bir öğe bulunamadı</span><span class="sxs-lookup"><span data-stu-id="e7f04-102">How to: Find an Element with a Specific Child Element (C#)</span></span>
<span data-ttu-id="e7f04-103">Bu konuda, belirli bir değeri olan bir alt öğesi olan belirli bir öğeyi bulmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7f04-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7f04-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7f04-104">Example</span></span>  
 <span data-ttu-id="e7f04-105">Örnek bulur `Test` sahip öğe bir `CommandLine` alt öğesi "Examp2.EXE" değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="e7f04-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="e7f04-106">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Test yapılandırmasını (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e7f04-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="e7f04-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e7f04-107">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="e7f04-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7f04-108">Example</span></span>  
 <span data-ttu-id="e7f04-109">Aşağıdaki örnek bir ad alanı XML aynı sorgu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7f04-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e7f04-110">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="e7f04-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="e7f04-111">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Test yapılandırmasında bir Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="e7f04-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="e7f04-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e7f04-112">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7f04-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7f04-113">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="e7f04-114">Temel sorgu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e7f04-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="e7f04-115">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="e7f04-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="e7f04-116">Projeksiyon işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="e7f04-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
