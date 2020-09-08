---
title: Öğe adlarını filtreleme-LINQ to XML
description: XElement IEnumerable döndüren bir yöntemi çağırdığınızda öğe adı üzerinde nasıl filtre yapacağınızı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 1f831fe0008c94b3956e93f3ced7176d8c0bf34e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552919"
---
# <a name="how-to-filter-on-element-names-linq-to-xml"></a><span data-ttu-id="e00d8-103">Öğe adlarını filtreleme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e00d8-103">How to filter on element names (LINQ to XML)</span></span>

<span data-ttu-id="e00d8-104">' In döndürdüğü yöntemlerden birini çağırdığınızda <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , öğe adı üzerinde filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e00d8-104">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>

## <a name="example-retrieve-descendants-filtered-to-a-specified-name"></a><span data-ttu-id="e00d8-105">Örnek: belirtilen ada göre filtrelenmiş alt öğeleri Al</span><span class="sxs-lookup"><span data-stu-id="e00d8-105">Example: Retrieve descendants filtered to a specified name</span></span>

<span data-ttu-id="e00d8-106">Bu örnek, yalnızca belirtilen ada sahip alt öğeleri içerecek şekilde filtrelenmiş alt öğelerin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="e00d8-106">This example retrieves a collection of descendants that's filtered to contain only descendants with the specified name.</span></span>

<span data-ttu-id="e00d8-107">Bu örnek, XML belgesi [örnek xml dosyasını kullanır: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="e00d8-107">This example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> items =
    from el in po.Descendants("ProductName")
    select el;
foreach(XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string) prdName);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim items As IEnumerable(Of XElement) = _
    From el In po...<ProductName> _
    Select el
For Each prdName As XElement In items
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
Next
```

<span data-ttu-id="e00d8-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e00d8-108">This example produces the following output:</span></span>

```output
ProductName:Lawnmower
ProductName:Baby Monitor
```

<span data-ttu-id="e00d8-109">Koleksiyonları döndüren diğer yöntemler <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> aynı kalıbı izler.</span><span class="sxs-lookup"><span data-stu-id="e00d8-109">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="e00d8-110">İmzaları <xref:System.Xml.Linq.XContainer.Elements%2A> ve ile benzerdir <xref:System.Xml.Linq.XContainer.Descendants%2A> .</span><span class="sxs-lookup"><span data-stu-id="e00d8-110">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="e00d8-111">Aşağıda benzer yöntem imzaları olan yöntemlerin tamamı listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="e00d8-111">The following is the complete list of methods that have similar method signatures:</span></span>

- <xref:System.Xml.Linq.XNode.Ancestors%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="e00d8-112">Örnek: bir ad alanında bulunan XML 'den alma</span><span class="sxs-lookup"><span data-stu-id="e00d8-112">Example: Retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="e00d8-113">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e00d8-113">The following example shows the same query for XML that's in a namespace.</span></span> <span data-ttu-id="e00d8-114">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e00d8-114">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="e00d8-115">Örnek, XML belgesi [örnek xml dosyası kullanır: bir ad alanında tipik satın alma siparişi](sample-xml-file-typical-purchase-order-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e00d8-115">The example uses XML document [Sample XML file: Typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
IEnumerable<XElement> items =
    from el in po.Descendants(aw + "ProductName")
    select el;
foreach (XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string)prdName);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim items As IEnumerable(Of XElement) = _
            From el In po...<aw:ProductName> _
            Select el
        For Each prdName As XElement In items
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
        Next
    End Sub
End Module
```

<span data-ttu-id="e00d8-116">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e00d8-116">This example produces the following output:</span></span>

```output
{http://www.adventure-works.com}ProductName:Lawnmower
{http://www.adventure-works.com}ProductName:Baby Monitor
```

## <a name="see-also"></a><span data-ttu-id="e00d8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e00d8-117">See also</span></span>

- [<span data-ttu-id="e00d8-118">LINQ to XML eksenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="e00d8-118">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
