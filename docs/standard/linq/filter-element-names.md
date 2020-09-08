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
# <a name="how-to-filter-on-element-names-linq-to-xml"></a>Öğe adlarını filtreleme (LINQ to XML)

' In döndürdüğü yöntemlerden birini çağırdığınızda <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , öğe adı üzerinde filtre uygulayabilirsiniz.

## <a name="example-retrieve-descendants-filtered-to-a-specified-name"></a>Örnek: belirtilen ada göre filtrelenmiş alt öğeleri Al

Bu örnek, yalnızca belirtilen ada sahip alt öğeleri içerecek şekilde filtrelenmiş alt öğelerin bir koleksiyonunu alır.

Bu örnek, XML belgesi [örnek xml dosyasını kullanır: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md).

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
ProductName:Lawnmower
ProductName:Baby Monitor
```

Koleksiyonları döndüren diğer yöntemler <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> aynı kalıbı izler. İmzaları <xref:System.Xml.Linq.XContainer.Elements%2A> ve ile benzerdir <xref:System.Xml.Linq.XContainer.Descendants%2A> . Aşağıda benzer yöntem imzaları olan yöntemlerin tamamı listelenmiştir:

- <xref:System.Xml.Linq.XNode.Ancestors%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a>Örnek: bir ad alanında bulunan XML 'den alma

Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

Örnek, XML belgesi [örnek xml dosyası kullanır: bir ad alanında tipik satın alma siparişi](sample-xml-file-typical-purchase-order-namespace.md).

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
{http://www.adventure-works.com}ProductName:Lawnmower
{http://www.adventure-works.com}ProductName:Baby Monitor
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md)
