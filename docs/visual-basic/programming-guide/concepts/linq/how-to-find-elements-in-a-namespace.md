---
title: "Nasıl yapılır: öğeleri Namespace (XPath-LINQ-XML) Bul (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7cb3b77-3424-4b54-9efa-4dc715948e41
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 257d4c37f849bbc50aac6b9cb4531d1084163db2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="fc149-102">Nasıl yapılır: öğeleri Namespace (XPath-LINQ-XML) Bul (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc149-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="fc149-103">XPath ifadeleri düğümleri belirli bir ad alanında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc149-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="fc149-104">XPath ifadelerinde ad alanı öneklerini ad alanları belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc149-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="fc149-105">Ad alanı öneklerini içeriyor bir XPath ifadesi ayrıştırmak için bir nesne uygulayan XPath yöntemleri için geçmesi gereken <xref:System.Xml.IXmlNamespaceResolver>.</span><span class="sxs-lookup"><span data-stu-id="fc149-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="fc149-106">Bu örnekte <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="fc149-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>  
  
 <span data-ttu-id="fc149-107">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="fc149-107">The XPath expression is:</span></span>  
  
 `./aw:*`  
  
## <a name="example"></a><span data-ttu-id="fc149-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc149-108">Example</span></span>  
 <span data-ttu-id="fc149-109">Aşağıdaki örnekte, iki ad alanı içeren bir XML ağacı okur.</span><span class="sxs-lookup"><span data-stu-id="fc149-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="fc149-110">Kullandığı bir <xref:System.Xml.XmlReader> XML belgesi okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="fc149-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="fc149-111">Ardından alır bir <xref:System.Xml.XmlNameTable> gelen <xref:System.Xml.XmlReader>ve bir <xref:System.Xml.XmlNamespaceManager> gelen <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="fc149-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="fc149-112">Kullandığı <xref:System.Xml.XmlNamespaceManager> öğeleri seçerken.</span><span class="sxs-lookup"><span data-stu-id="fc149-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>  
  
```vb  
Dim reader As XmlReader = _  
        XmlReader.Create("ConsolidatedPurchaseOrders.xml")  
Dim root As XElement = XElement.Load(reader)  
Dim nameTable As XmlNameTable = reader.NameTable  
Dim namespaceManager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com")  
  
Dim list1 As IEnumerable(Of XElement) = _  
        root.XPathSelectElements("./aw:*", namespaceManager)  
Dim list2 As IEnumerable(Of XElement) = _  
    From el In root.Elements() _  
    Where el.Name.Namespace = "http://www.adventure-works.com" _  
    Select el  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="fc149-113">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="fc149-113">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fc149-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc149-114">See Also</span></span>  
 [<span data-ttu-id="fc149-115">LINQ-XML XPath kullanıcıların (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc149-115">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
