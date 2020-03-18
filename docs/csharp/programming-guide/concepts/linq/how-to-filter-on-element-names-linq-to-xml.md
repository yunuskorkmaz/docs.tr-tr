---
title: Eleman adlarına nasıl filtre yapılır (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 74efb19ef5ec77ca29145d27a8e5aa977530b68b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141268"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="8af57-102">Eleman adlarına nasıl filtre yapılır (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8af57-102">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8af57-103">Döndürülen <xref:System.Collections.Generic.IEnumerable%601> yöntemlerden birini <xref:System.Xml.Linq.XElement>aradiğinizde, öğe adına filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8af57-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8af57-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8af57-104">Example</span></span>  
 <span data-ttu-id="8af57-105">Bu örnek, yalnızca belirtilen ada sahip torunları içerecek şekilde filtre uygulanmış bir soyundan gelenler koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="8af57-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="8af57-106">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Tipik SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="8af57-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="8af57-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8af57-107">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="8af57-108">Koleksiyonların <xref:System.Xml.Linq.XElement> döndürülen <xref:System.Collections.Generic.IEnumerable%601> diğer yöntemleri de aynı şekilde izler.</span><span class="sxs-lookup"><span data-stu-id="8af57-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="8af57-109">İmzaları benzer <xref:System.Xml.Linq.XContainer.Elements%2A> ve. <xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="8af57-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="8af57-110">Benzer yöntem imzalarına sahip yöntemlerin tam listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8af57-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="8af57-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8af57-111">Example</span></span>  
 <span data-ttu-id="8af57-112">Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8af57-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="8af57-113">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8af57-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="8af57-114">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında Tipik Satın Alma Siparişi.](./sample-xml-file-typical-purchase-order-in-a-namespace.md)</span><span class="sxs-lookup"><span data-stu-id="8af57-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="8af57-115">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8af57-115">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="8af57-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8af57-116">See also</span></span>

- [<span data-ttu-id="8af57-117">LINQ - XML Eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="8af57-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
