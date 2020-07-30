---
title: Ad alanındaki tüm düğümleri bulma (C#)
description: Bu ad alanındaki tüm düğümleri bulmak için her öğe veya özniteliğin ad alanı üzerinde nasıl filtre yapacağınızı öğrenin.
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: bf739480c6b4e2c53d5c430d47ff833e8995f6a4
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303315"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="31e41-103">Ad alanındaki tüm düğümleri bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="31e41-103">How to find all nodes in a namespace (C#)</span></span>
<span data-ttu-id="31e41-104">Söz konusu ad alanındaki tüm düğümleri bulmak için her öğe veya özniteliğin ad alanı üzerinde filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31e41-104">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31e41-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="31e41-105">Example</span></span>  
 <span data-ttu-id="31e41-106">Aşağıdaki örnek iki ad alanı olan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="31e41-106">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="31e41-107">Daha sonra ağaç üzerinde dolaşır ve bu ad alanlarından birindeki tüm öğelerin ve özniteliklerin adlarını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="31e41-107">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
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
  
 <span data-ttu-id="31e41-108">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="31e41-108">This code produces the following output:</span></span>  
  
```output  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="31e41-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="31e41-109">Example</span></span>  
 <span data-ttu-id="31e41-110">Aşağıdaki sorgu tarafından erişilen XML dosyası, satın alma emirlerini iki farklı ad alanında içerir.</span><span class="sxs-lookup"><span data-stu-id="31e41-110">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="31e41-111">Sorgu, yalnızca ad alanlarından birindeki öğeleri içeren yeni bir ağaç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="31e41-111">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="31e41-112">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: birleştirilmiş satın alma siparişleri](./sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="31e41-112">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](./sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
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
  
 <span data-ttu-id="31e41-113">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="31e41-113">This code produces the following output:</span></span>  
  
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
