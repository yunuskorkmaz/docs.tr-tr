---
title: XPath (C#) kullanarak LINQ'yi XML'e sorgulama
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 61878febd9b4880872b7bc58e4de04b37cff96f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344805"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="4462d-102">XPath (C#) kullanarak LINQ'yi XML'e sorgulama</span><span class="sxs-lookup"><span data-stu-id="4462d-102">How to query LINQ to XML using XPath (C#)</span></span>
<span data-ttu-id="4462d-103">Bu konu, XPath kullanarak bir XML ağacısorgulamasağlayan uzantı yöntemlerini tanır.</span><span class="sxs-lookup"><span data-stu-id="4462d-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="4462d-104">Bu uzantı yöntemlerini kullanma <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>hakkında ayrıntılı bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="4462d-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="4462d-105">XPath'i kullanmak için çok özel bir nedeniniz yoksa, örneğin eski kodun yaygın kullanımı gibi, XPath'i LINQ ile XML'e kullanmak önerilmez.</span><span class="sxs-lookup"><span data-stu-id="4462d-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="4462d-106">XPath sorguları sorguları kadar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] iyi performans göstermez.</span><span class="sxs-lookup"><span data-stu-id="4462d-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4462d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4462d-107">Example</span></span>  
 <span data-ttu-id="4462d-108">Aşağıdaki örnek küçük bir XML ağacı <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> oluşturur ve bir öğe kümesi seçmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4462d-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="4462d-109">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4462d-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  