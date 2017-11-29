---
title: "Nasıl yapılır: LINQ-XML XPath (C#) kullanarak sorgulama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1cb47b5b4b85536feeb5006fe6dd31580ca651b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="ecf27-102">Nasıl yapılır: LINQ-XML XPath (C#) kullanarak sorgulama</span><span class="sxs-lookup"><span data-stu-id="ecf27-102">How to: Query LINQ to XML Using XPath (C#)</span></span>
<span data-ttu-id="ecf27-103">Bu konu, bir XML ağacı XPath kullanarak sorgula sağlayan genişletme yöntemleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="ecf27-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="ecf27-104">Bu uzantı yöntemleri kullanma hakkında ayrıntılı bilgi için bkz: <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ecf27-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="ecf27-105">Kullanarak sorgulamak için çok özel bir nedeniniz yoksa XPath, LINQ-XML XPath kullanarak eski kod kapsamlı kullanımını gibi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="ecf27-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="ecf27-106">XPath sorguları değil gerçekleştirecek yanı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="ecf27-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecf27-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="ecf27-107">Example</span></span>  
 <span data-ttu-id="ecf27-108">Aşağıdaki örnekte küçük bir XML ağacı oluşturduğu ve kullandığı <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> bir grup öğeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="ecf27-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="ecf27-109">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="ecf27-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ecf27-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ecf27-110">See Also</span></span>  
 [<span data-ttu-id="ecf27-111">Gelişmiş sorgu teknikler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ecf27-111">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
