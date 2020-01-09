---
title: XPath (C#) kullanarak LINQ to XML sorgulama
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 61878febd9b4880872b7bc58e4de04b37cff96f8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344805"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="bfc15-102">XPath (C#) kullanarak LINQ to XML sorgulama</span><span class="sxs-lookup"><span data-stu-id="bfc15-102">How to query LINQ to XML using XPath (C#)</span></span>
<span data-ttu-id="bfc15-103">Bu konu, XPath kullanarak bir XML ağacını sorgulamanızı sağlayan uzantı yöntemlerini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="bfc15-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="bfc15-104">Bu uzantı yöntemlerini kullanma hakkında ayrıntılı bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfc15-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="bfc15-105">Eski kodun kapsamlı kullanımı gibi XPath kullanarak sorgulamak için çok özel bir nedeniniz yoksa LINQ to XML ile XPath kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="bfc15-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="bfc15-106">XPath sorguları, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorguları da gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="bfc15-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfc15-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfc15-107">Example</span></span>  
 <span data-ttu-id="bfc15-108">Aşağıdaki örnek küçük bir XML ağacı oluşturur ve bir öğe kümesi seçmek için <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="bfc15-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="bfc15-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bfc15-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  