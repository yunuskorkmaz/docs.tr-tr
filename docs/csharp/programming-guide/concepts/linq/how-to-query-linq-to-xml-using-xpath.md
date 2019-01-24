---
title: 'Nasıl yapılır: LINQ to XML XPath kullanarak sorgula (C#)'
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: a3e9cb29b9ba027cfc70eeb0cd163b24834dff83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564113"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="79cb7-102">Nasıl yapılır: LINQ to XML XPath kullanarak sorgula (C#)</span><span class="sxs-lookup"><span data-stu-id="79cb7-102">How to: Query LINQ to XML Using XPath (C#)</span></span>
<span data-ttu-id="79cb7-103">Bu konu, bir XML ağacı XPath kullanarak sorgula olanak tanıyan uzantı yöntemleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="79cb7-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="79cb7-104">Bu uzantı yöntemleri kullanma hakkında ayrıntılı bilgi için bkz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="79cb7-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="79cb7-105">Kullanarak sorgulamak için çok özel bir nedeniniz yoksa, XPath XPath ile LINQ to XML kullanarak eski kod kapsamlı kullanımını gibi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="79cb7-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="79cb7-106">XPath sorguları gerçekleştirme yanı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="79cb7-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79cb7-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="79cb7-107">Example</span></span>  
 <span data-ttu-id="79cb7-108">Aşağıdaki örnek, küçük bir XML ağacı oluşturur ve kullanır <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> öğe kümesini seçin.</span><span class="sxs-lookup"><span data-stu-id="79cb7-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="79cb7-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="79cb7-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79cb7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79cb7-110">See also</span></span>

- [<span data-ttu-id="79cb7-111">Gelişmiş sorgu teknikleri (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="79cb7-111">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
