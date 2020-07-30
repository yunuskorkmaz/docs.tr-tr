---
title: Öğe adlarını filtreleme (LINQ to XML) (C#)
description: XElement IEnumerable döndüren bir yöntemi çağırdığınızda öğe adında filtre yapmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: be660a69b8d860ad907661ce17002379b8842121
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301755"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="1f402-103">Öğe adlarını filtreleme (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1f402-103">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="1f402-104">' In döndürdüğü yöntemlerden birini çağırdığınızda <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , öğe adı üzerinde filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f402-104">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f402-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f402-105">Example</span></span>  
 <span data-ttu-id="1f402-106">Bu örnek, yalnızca belirtilen ada sahip alt öğeleri içerecek şekilde filtrelenen alt öğelerin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="1f402-106">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="1f402-107">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="1f402-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="1f402-108">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1f402-108">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="1f402-109">Koleksiyonları döndüren diğer yöntemler <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> aynı kalıbı izler.</span><span class="sxs-lookup"><span data-stu-id="1f402-109">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="1f402-110">İmzaları <xref:System.Xml.Linq.XContainer.Elements%2A> ve ile benzerdir <xref:System.Xml.Linq.XContainer.Descendants%2A> .</span><span class="sxs-lookup"><span data-stu-id="1f402-110">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="1f402-111">Aşağıda benzer yöntem imzaları olan yöntemlerin tamamı listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="1f402-111">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="1f402-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f402-112">Example</span></span>  
 <span data-ttu-id="1f402-113">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f402-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1f402-114">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1f402-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="1f402-115">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında tipik satın alma siparişi](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="1f402-115">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="1f402-116">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1f402-116">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f402-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f402-117">See also</span></span>

- [<span data-ttu-id="1f402-118">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="1f402-118">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
