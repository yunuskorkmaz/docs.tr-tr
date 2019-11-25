---
title: Bir ad alanında öğeleri bulma (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: da9d819be5234a2429b6eab276f89bd0d877d4a7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141075"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a>Bir ad alanında öğeleri bulma (XPath-LINQ to XML) (C#)

XPath ifadeleri, belirli bir ad alanındaki düğümleri bulabilir. XPath ifadeleri ad alanlarını belirtmek için ad alanı öneklerini kullanır. Ad alanı önekleri içeren bir XPath ifadesini ayrıştırmak için, <xref:System.Xml.IXmlNamespaceResolver>uygulayan XPath yöntemlerine bir nesne geçirmeniz gerekir. Bu örnek <xref:System.Xml.XmlNamespaceManager>kullanır.

XPath ifadesi:

`./aw:*`

## <a name="example"></a>Örnek

Aşağıdaki örnek, iki ad alanı içeren bir XML ağacını okur. XML belgesini okumak için bir <xref:System.Xml.XmlReader> kullanır. Daha sonra <xref:System.Xml.XmlReader>ve <xref:System.Xml.XmlNameTable><xref:System.Xml.XmlNamespaceManager> bir <xref:System.Xml.XmlNameTable> alır. Öğeleri seçerken <xref:System.Xml.XmlNamespaceManager> kullanır.

```csharp
XmlReader reader = XmlReader.Create("ConsolidatedPurchaseOrders.xml");
XElement root = XElement.Load(reader);
XmlNameTable nameTable = reader.NameTable;
XmlNamespaceManager namespaceManager = new XmlNamespaceManager(nameTable);
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com");
IEnumerable<XElement> list1 = root.XPathSelectElements("./aw:*", namespaceManager);
IEnumerable<XElement> list2 =
    from el in root.Elements()
    where el.Name.Namespace == "http://www.adventure-works.com"
    select el;
if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Results are identical
<aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">
    <aw:ShippingAddress>
      <aw:Name>Chris Preston</aw:Name>
      <aw:Street>123 Main St.</aw:Street>
      <aw:City>Seattle</aw:City>
      <aw:State>WA</aw:State>
      <aw:Zip>98113</aw:Zip>
      <aw:Country>USA</aw:Country>
    </aw:ShippingAddress>
    <aw:BillingAddress>
      <aw:Name>Chris Preston</aw:Name>
      <aw:Street>123 Main St.</aw:Street>
      <aw:City>Seattle</aw:City>
      <aw:State>WA</aw:State>
      <aw:Zip>98113</aw:Zip>
      <aw:Country>USA</aw:Country>
    </aw:BillingAddress>
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>
    <aw:Item PartNum="LIT-01">
      <aw:ProductID>Litware Networking Card</aw:ProductID>
      <aw:Qty>1</aw:Qty>
      <aw:Price>20.99</aw:Price>
    </aw:Item>
    <aw:Item PartNum="LIT-25">
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>
      <aw:Qty>1</aw:Qty>
      <aw:Price>199.99</aw:Price>
    </aw:Item>
  </aw:PurchaseOrder>
```
