---
title: 'Nasıl yapılır: Bir ad alanındaki tüm düğümleri bul (C#)'
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: 512ca398831541c30a6c0c1e305c5c6269c13ddb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593645"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="28aa1-102">Nasıl yapılır: Bir ad alanındaki tüm düğümleri bul (C#)</span><span class="sxs-lookup"><span data-stu-id="28aa1-102">How to: Find All Nodes in a Namespace (C#)</span></span>
<span data-ttu-id="28aa1-103">Söz konusu ad alanındaki tüm düğümleri bulmak için her öğe veya özniteliğin ad alanı üzerinde filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28aa1-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28aa1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="28aa1-104">Example</span></span>  
 <span data-ttu-id="28aa1-105">Aşağıdaki örnek iki ad alanı olan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28aa1-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="28aa1-106">Daha sonra ağaç üzerinde dolaşır ve bu ad alanlarından birindeki tüm öğelerin ve özniteliklerin adlarını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="28aa1-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
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
  
 <span data-ttu-id="28aa1-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="28aa1-107">This code produces the following output:</span></span>  
  
```  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="28aa1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="28aa1-108">Example</span></span>  
 <span data-ttu-id="28aa1-109">Aşağıdaki sorgu tarafından erişilen XML dosyası, satın alma emirlerini iki farklı ad alanında içerir.</span><span class="sxs-lookup"><span data-stu-id="28aa1-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="28aa1-110">Sorgu, yalnızca ad alanlarından birindeki öğeleri içeren yeni bir ağaç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28aa1-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="28aa1-111">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Birleştirilmiş satın alma](./sample-xml-file-consolidated-purchase-orders.md)siparişleri.</span><span class="sxs-lookup"><span data-stu-id="28aa1-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](./sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
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
  
 <span data-ttu-id="28aa1-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="28aa1-112">This code produces the following output:</span></span>  
  
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
