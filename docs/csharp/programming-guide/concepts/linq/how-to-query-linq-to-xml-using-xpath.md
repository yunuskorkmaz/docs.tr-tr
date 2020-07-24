---
title: XPath kullanarak LINQ to XML sorgulama (C#)
description: XPath kullanarak bir XML ağacını sorgulamak Için C# ' de uzantı yöntemlerini kullanabilirsiniz. Genel olarak, LINQ to XML ile XPath kullanılması önerilmez.
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: fff45a93380b5af85aa640fc690783cc95e6298b
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104349"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="e5724-104">XPath kullanarak LINQ to XML sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="e5724-104">How to query LINQ to XML using XPath (C#)</span></span>
<span data-ttu-id="e5724-105">Bu konu, XPath kullanarak bir XML ağacını sorgulamanızı sağlayan uzantı yöntemlerini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="e5724-105">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="e5724-106">Bu uzantı yöntemlerini kullanma hakkında ayrıntılı bilgi için bkz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> ..</span><span class="sxs-lookup"><span data-stu-id="e5724-106">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e5724-107">Eski kodun kapsamlı kullanımı gibi XPath kullanarak sorgulamak için çok özel bir nedeniniz yoksa LINQ to XML ile XPath kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="e5724-107">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="e5724-108">XPath sorguları, sorgu ve sorgular gerçekleştirmeyecektir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e5724-108">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5724-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5724-109">Example</span></span>  
 <span data-ttu-id="e5724-110">Aşağıdaki örnek küçük bir XML ağacı oluşturur ve <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> bir öğe kümesi seçmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5724-110">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="e5724-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e5724-111">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  