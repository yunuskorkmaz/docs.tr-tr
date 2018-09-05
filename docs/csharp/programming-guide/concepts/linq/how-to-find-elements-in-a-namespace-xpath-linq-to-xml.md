---
title: 'Nasıl yapılır: bir Namespace (XPath-LINQ to XML) alanındaki öğeleri bulma (C#)'
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: a0375641f9f5e75c51fe27936c07c32020e5dc0d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505751"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a>Nasıl yapılır: bir Namespace (XPath-LINQ to XML) alanındaki öğeleri bulma (C#)
XPath ifadeleri düğüm, belirli bir ad alanında bulabilirsiniz. XPath ifadeleri, ad alanı öneklerini ad alanları belirtmek için kullanın. Ad alanı öneklerini içeren bir XPath ifadesi ayrıştırılamadı XPath yöntemlere uygulayan bir nesne geçmelidir. <xref:System.Xml.IXmlNamespaceResolver>. Bu örnekte <xref:System.Xml.XmlNamespaceManager>.  
  
 XPath ifadesidir:  
  
 `./aw:*`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki ad alanları içeren bir XML ağacı okur. Bunu kullanan bir <xref:System.Xml.XmlReader> XML belgesi okumak için. Ardından alır bir <xref:System.Xml.XmlNameTable> gelen <xref:System.Xml.XmlReader>ve bir <xref:System.Xml.XmlNamespaceManager> gelen <xref:System.Xml.XmlNameTable>. Kullandığı <xref:System.Xml.XmlNamespaceManager> öğeleri seçerken.  
  
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
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [LINQ to XML için XPath kullanıcıları (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
