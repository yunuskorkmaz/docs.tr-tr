---
title: 'Nasıl yapılır: Öğe adlarını filtrele (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 2a4eccac3bc24005af0efee0785393de00039228
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253814"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="a81c8-102">Nasıl yapılır: Öğe adlarını filtrele (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a81c8-102">How to: Filter on Element Names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="a81c8-103">' In <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>döndürdüğü yöntemlerden birini çağırdığınızda, öğe adı üzerinde filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a81c8-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a81c8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a81c8-104">Example</span></span>  
 <span data-ttu-id="a81c8-105">Bu örnek, yalnızca belirtilen ada sahip alt öğeleri içerecek şekilde filtrelenen alt öğelerin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="a81c8-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="a81c8-106">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)).</span><span class="sxs-lookup"><span data-stu-id="a81c8-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="a81c8-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a81c8-107">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="a81c8-108">Koleksiyonları<xref:System.Xml.Linq.XElement> döndüren <xref:System.Collections.Generic.IEnumerable%601> diğer yöntemler aynı kalıbı izler.</span><span class="sxs-lookup"><span data-stu-id="a81c8-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="a81c8-109">İmzaları <xref:System.Xml.Linq.XContainer.Elements%2A> ve ile <xref:System.Xml.Linq.XContainer.Descendants%2A>benzerdir.</span><span class="sxs-lookup"><span data-stu-id="a81c8-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="a81c8-110">Aşağıda benzer yöntem imzaları olan yöntemlerin tamamı listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="a81c8-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="a81c8-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a81c8-111">Example</span></span>  
 <span data-ttu-id="a81c8-112">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a81c8-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a81c8-113">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a81c8-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a81c8-114">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Bir ad alanında](./sample-xml-file-typical-purchase-order-in-a-namespace.md)tipik satın alma siparişi.</span><span class="sxs-lookup"><span data-stu-id="a81c8-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="a81c8-115">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a81c8-115">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="a81c8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a81c8-116">See also</span></span>

- [<span data-ttu-id="a81c8-117">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="a81c8-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
