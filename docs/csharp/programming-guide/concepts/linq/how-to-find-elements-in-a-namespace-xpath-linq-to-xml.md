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
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a><span data-ttu-id="ddf3b-102">Bir ad alanında öğeleri bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ddf3b-102">How to find elements in a namespace (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="ddf3b-103">XPath ifadeleri, belirli bir ad alanındaki düğümleri bulabilir.</span><span class="sxs-lookup"><span data-stu-id="ddf3b-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="ddf3b-104">XPath ifadeleri ad alanlarını belirtmek için ad alanı öneklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddf3b-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="ddf3b-105">Ad alanı önekleri içeren bir XPath ifadesini ayrıştırmak için, <xref:System.Xml.IXmlNamespaceResolver>uygulayan XPath yöntemlerine bir nesne geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ddf3b-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="ddf3b-106">Bu örnek <xref:System.Xml.XmlNamespaceManager>kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddf3b-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>

<span data-ttu-id="ddf3b-107">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="ddf3b-107">The XPath expression is:</span></span>

`./aw:*`

## <a name="example"></a><span data-ttu-id="ddf3b-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddf3b-108">Example</span></span>

<span data-ttu-id="ddf3b-109">Aşağıdaki örnek, iki ad alanı içeren bir XML ağacını okur.</span><span class="sxs-lookup"><span data-stu-id="ddf3b-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="ddf3b-110">XML belgesini okumak için bir <xref:System.Xml.XmlReader> kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddf3b-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="ddf3b-111">Daha sonra <xref:System.Xml.XmlReader>ve <xref:System.Xml.XmlNameTable><xref:System.Xml.XmlNamespaceManager> bir <xref:System.Xml.XmlNameTable> alır.</span><span class="sxs-lookup"><span data-stu-id="ddf3b-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="ddf3b-112">Öğeleri seçerken <xref:System.Xml.XmlNamespaceManager> kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddf3b-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>

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

<span data-ttu-id="ddf3b-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ddf3b-113">This example produces the following output:</span></span>

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
