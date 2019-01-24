---
title: 'Nasıl yapılır: Bir Namespace tüm düğümleri bulma (C#)'
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: 3d9a2780a5241bdc535938cb182441418346755f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524656"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="aadfe-102">Nasıl yapılır: Bir Namespace tüm düğümleri bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="aadfe-102">How to: Find All Nodes in a Namespace (C#)</span></span>
<span data-ttu-id="aadfe-103">Her bir öğe veya öznitelik, belirli bir ad alanındaki tüm düğümleri bulmak için ad alanı filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aadfe-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aadfe-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="aadfe-104">Example</span></span>  
 <span data-ttu-id="aadfe-105">Aşağıdaki örnek, bir XML ağacı ile iki ad alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aadfe-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="aadfe-106">Ağacı ile yineleme ve tüm öğeleri ve öznitelikleri o ad alanlarından birinde adlarını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="aadfe-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
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
  
 <span data-ttu-id="aadfe-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aadfe-107">This code produces the following output:</span></span>  
  
```  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="aadfe-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="aadfe-108">Example</span></span>  
 <span data-ttu-id="aadfe-109">Aşağıdaki sorgu tarafından erişilen XML dosyasını iki farklı ad alanlarında, satın alma siparişleri içerir.</span><span class="sxs-lookup"><span data-stu-id="aadfe-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="aadfe-110">Sorgu yalnızca öğeleri ad alanlarından birinde yeni bir ağaç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aadfe-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="aadfe-111">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Birleştirilmiş satın alma siparişleri](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="aadfe-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
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
  
 <span data-ttu-id="aadfe-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aadfe-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aadfe-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aadfe-113">See also</span></span>

- [<span data-ttu-id="aadfe-114">Temel sorgular (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="aadfe-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
