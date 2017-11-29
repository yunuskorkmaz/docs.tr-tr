---
title: "Nasıl yapılır: bir Namespace (Visual Basic) tüm düğümleri Bul"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b735d7da-5727-48a3-ab57-a16378adc32e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8664d29e27673e1ad08d3d72b29d8dc9c711a9fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-all-nodes-in-a-namespace-visual-basic"></a><span data-ttu-id="dde52-102">Nasıl yapılır: bir Namespace (Visual Basic) tüm düğümleri Bul</span><span class="sxs-lookup"><span data-stu-id="dde52-102">How to: Find All Nodes in a Namespace (Visual Basic)</span></span>
<span data-ttu-id="dde52-103">Her bir öğe veya öznitelik bu belirli ad alanındaki tüm düğümleri bulmak için ad alanı filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dde52-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dde52-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="dde52-104">Example</span></span>  
 <span data-ttu-id="dde52-105">Aşağıdaki örnekte, iki ad alanı ile bir XML ağaç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dde52-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="dde52-106">Ağacı ile yineleme ve tüm öğeleri ve bu ad alanlarından birinde özniteliklerinin adları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="dde52-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
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
  
 <span data-ttu-id="dde52-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="dde52-107">This code produces the following output:</span></span>  
  
```  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="dde52-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="dde52-108">Example</span></span>  
 <span data-ttu-id="dde52-109">Aşağıdaki sorgu tarafından erişilen XML dosyası iki farklı ad alanlarında satınalma siparişleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dde52-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="dde52-110">Sorgu yeni bir ağaç öğeleriyle yalnızca ad alanlarından birinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dde52-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="dde52-111">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: birleştirilmiş satınalma siparişi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="dde52-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
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
  
 <span data-ttu-id="dde52-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="dde52-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dde52-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dde52-113">See Also</span></span>  
 [<span data-ttu-id="dde52-114">Temel sorgu (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dde52-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
