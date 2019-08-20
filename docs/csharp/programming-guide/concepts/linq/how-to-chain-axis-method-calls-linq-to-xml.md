---
title: 'Nasıl yapılır: Zincir ekseni Yöntem çağrıları (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 573efb50dd889d1e10fc3a74bb5c7d9a8ac30eab
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594086"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="b859d-102">Nasıl yapılır: Zincir ekseni Yöntem çağrıları (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b859d-102">How to: Chain Axis Method Calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b859d-103">Kodunuzda kullanacağınız ortak bir model, bir eksen yöntemi çağırmak ve sonra uzantı yöntemi eksenlerinden birini çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b859d-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="b859d-104">Adında `Elements` bir öğe koleksiyonu döndüren iki eksen vardır <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> : yöntemi ve <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b859d-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b859d-105">Ağaçta verilen bir derinlikte belirtilen bir adın tüm öğelerini bulmak için bu iki ekseni birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b859d-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b859d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b859d-106">Example</span></span>  
 <span data-ttu-id="b859d-107">Bu örnek, <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> tüm <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> öğelerinde tüm öğelerdeki `Name` tüm öğeleri `Address` `PurchaseOrder` bulmak için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="b859d-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="b859d-108">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Birden çok satın alma siparişi (](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="b859d-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="b859d-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b859d-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="b859d-110">Bu, `Elements` eksenin uygulamalarından biri <xref:System.Xml.Linq.XContainer>üzerinde <xref:System.Collections.Generic.IEnumerable%601> bir genişletme yöntemi olduğu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b859d-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="b859d-111"><xref:System.Xml.Linq.XElement>' dan <xref:System.Xml.Linq.XContainer>türetilir, bu sayede yöntemine yapılan <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> çağrının <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> sonuçlarında yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b859d-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b859d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b859d-112">Example</span></span>  
 <span data-ttu-id="b859d-113">Bazı durumlarda, üst öğelerinden oluşan veya aradaki bir işlem olduğunda, belirli bir öğe derinliğinde tüm öğeleri almak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b859d-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="b859d-114">Örneğin, aşağıdaki belgede, öğesinin alt öğesi olan `ConfigParameter` tüm öğeleri `Customer` almak isteyebilirsiniz, ancak `ConfigParameter` `Root` öğesinin bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="b859d-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="b859d-115">Bunu yapmak için, aşağıdaki gibi, <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> eksenini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b859d-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="b859d-116">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b859d-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="b859d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b859d-117">Example</span></span>  
 <span data-ttu-id="b859d-118">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı tekniği gösterir.</span><span class="sxs-lookup"><span data-stu-id="b859d-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="b859d-119">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b859d-119">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b859d-120">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Bir ad alanında](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md)birden fazla satın alma siparişi.</span><span class="sxs-lookup"><span data-stu-id="b859d-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="b859d-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b859d-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b859d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b859d-122">See also</span></span>

- [<span data-ttu-id="b859d-123">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b859d-123">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes.md)
