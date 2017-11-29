---
title: "Nasıl yapılır: LINQ-XML (Visual Basic) XPath kullanarak sorgula"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97f885a76a79832b06f2f5d4a270d418bf244cb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="11105-102">Nasıl yapılır: LINQ-XML (Visual Basic) XPath kullanarak sorgula</span><span class="sxs-lookup"><span data-stu-id="11105-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="11105-103">Bu konu, bir XML ağacı XPath kullanarak sorgula sağlayan genişletme yöntemleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="11105-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="11105-104">Bu uzantı yöntemleri kullanma hakkında ayrıntılı bilgi için bkz: <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="11105-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="11105-105">Kullanarak sorgulamak için çok özel bir nedeniniz yoksa XPath, LINQ-XML XPath kullanarak eski kod kapsamlı kullanımını gibi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="11105-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="11105-106">XPath sorguları değil gerçekleştirecek yanı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="11105-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11105-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="11105-107">Example</span></span>  
 <span data-ttu-id="11105-108">Aşağıdaki örnekte küçük bir XML ağacı oluşturduğu ve kullandığı <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> bir grup öğeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="11105-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="11105-109">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="11105-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11105-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11105-110">See Also</span></span>  
 [<span data-ttu-id="11105-111">Gelişmiş sorgu teknikler (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11105-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
