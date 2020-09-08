---
title: Ad alanındaki tüm düğümleri bulma-LINQ to XML
description: Söz konusu ad alanındaki tüm düğümleri bulmak için her öğe veya özniteliğin ad alanı üzerinde filtre uygulayabilirsiniz.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: 2041afc3e061aa89e9be5832c9d6fd5bab7a38d8
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552902"
---
# <a name="how-to-find-all-nodes-in-a-namespace-linq-to-xml"></a>Ad alanındaki tüm düğümleri bulma (LINQ to XML)

Söz konusu ad alanındaki tüm düğümleri bulmak için her öğe veya özniteliğin ad alanı üzerinde filtre uygulayabilirsiniz.

## <a name="example-create-an-xml-tree-with-two-namespaces-and-print-contents-of-one"></a>Örnek: iki ad alanı olan bir XML ağacı oluşturma ve içeriğini yazdırma

Aşağıdaki örnek iki ad alanı olan bir XML ağacı oluşturur. Daha sonra ağaç üzerinde dolaşır ve bu ad alanlarından birindeki tüm öğelerin ve özniteliklerin adlarını yazdırır.

```csharp
string markup = @"<aw:Root xmlns:aw='http://www.adventure-works.com' xmlns:fc='www.fourthcoffee.com'>
  <fc:Child1>abc</fc:Child1>
  <fc:Child2>def</fc:Child2>
  <aw:Child3>ghi</aw:Child3>
  <fc:Child4>
    <fc:GrandChild1>jkl</fc:GrandChild1>
    <aw:GrandChild2>mno</aw:GrandChild2>
  </fc:Child4>
</aw:Root>";
XElement xmlTree = XElement.Parse(markup);
Console.WriteLine("Nodes in the http://www.adventure-works.com namespace");
IEnumerable<XElement> awElements =
    from el in xmlTree.Descendants()
    where el.Name.Namespace == "http://www.adventure-works.com"
    select el;
foreach (XElement el in awElements)
    Console.WriteLine(el.Name.ToString());
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1
    Sub Main()
        Dim xmlTree As XElement = _
            <aw:Root>
                <fc:Child1>abc</fc:Child1>
                <fc:Child2>def</fc:Child2>
                <aw:Child3>ghi</aw:Child3>
                <fc:Child4>
                    <fc:GrandChild1>jkl</fc:GrandChild1>
                    <aw:GrandChild2>mno</aw:GrandChild2>
                </fc:Child4>
            </aw:Root>
        Console.WriteLine("Nodes in the http://www.adventure-works.com namespace")
        Dim awElements As IEnumerable(Of XElement) = _
            From el In xmlTree.Descendants() _
            Where (el.Name.Namespace = GetXmlNamespace(aw)) _
            Select el
        For Each el As XElement In awElements
            Console.WriteLine(el.Name.ToString())
        Next
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Nodes in the http://www.adventure-works.com namespace
{http://www.adventure-works.com}Child3
{http://www.adventure-works.com}GrandChild2
```

## <a name="example-create-an-xml-tree-from-one-of-two-namespaces-contained-in-a-file"></a>Örnek: bir dosyada bulunan iki ad alanından birinden bir XML ağacı oluşturma

XML belgesi [örnek xml dosyası: birleştirilmiş satın alma siparişleri](sample-xml-file-consolidated-purchase-orders.md) , satın alma siparişlerini iki farklı ad alanında içerir. Aşağıdaki sorgu, öğelerinden birinin öğelerinden yeni bir ağaç oluşturur.

```csharp
XDocument cpo = XDocument.Load("ConsolidatedPurchaseOrders.xml");
XNamespace aw = "http://www.adventure-works.com";
XElement newTree = new XElement("Root",
    from el in cpo.Root.Elements()
    where el.Name.Namespace == aw
    select el
);
Console.WriteLine(newTree);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim cpo As XDocument = XDocument.Load("ConsolidatedPurchaseOrders.xml")
        Dim newTree As XElement = _
            <Root>
                <%= From el In cpo.Root.Elements() _
                    Where el.Name.Namespace = GetXmlNamespace(aw) _
                    Select el %>
            </Root>
        Console.WriteLine(newTree)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root>
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
</Root>
```
