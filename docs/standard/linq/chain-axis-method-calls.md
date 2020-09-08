---
title: Eksen yöntemi çağrılarını zincirle-LINQ to XML
description: Ağaçtaki belirli bir derinlikte belirtilen bir adın tüm öğelerini bulmak için XContainer. Elements ve Extensions. Elements yöntemlerini nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 23d3b5a3dacbc56a570a92178cb8e28482907ca1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553494"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml"></a><span data-ttu-id="e2443-103">Zincir eksen yöntem çağrıları (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e2443-103">How to chain axis method calls (LINQ to XML)</span></span>

<span data-ttu-id="e2443-104">Kodunuzda kullanacağınız ortak bir model, bir eksen yöntemi çağırmak ve sonra uzantı yöntemi eksenlerinden birini çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2443-104">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>

<span data-ttu-id="e2443-105">Adında `Elements` bir öğe koleksiyonu döndüren iki eksen vardır: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yöntemi ve <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e2443-105">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e2443-106">Ağaçta verilen bir derinlikte belirtilen bir adın tüm öğelerini bulmak için bu iki ekseni birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2443-106">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>

## <a name="example-retrieve-all-name-elements"></a><span data-ttu-id="e2443-107">Örnek: tüm ad öğelerini Al</span><span class="sxs-lookup"><span data-stu-id="e2443-107">Example: Retrieve all name elements</span></span>

<span data-ttu-id="e2443-108">Bu örnek, tüm öğelerinde tüm öğelerin tüm öğelerini <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> almak için ve kullanır `Name` `Address` `PurchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="e2443-108">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to retrieve all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>

<span data-ttu-id="e2443-109">Bu örnek, XML belgesi [örnek xml dosyasını kullanır: birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="e2443-109">This example uses XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

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

```vb
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")
Dim names As IEnumerable(Of XElement) = _
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _
    Select el
For Each e As XElement In names
    Console.WriteLine(e)
Next
```

<span data-ttu-id="e2443-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e2443-110">This example produces the following output:</span></span>

```xml
<Name>Ellen Adams</Name>
<Name>Tai Yee</Name>
<Name>Cristian Osorio</Name>
<Name>Cristian Osorio</Name>
<Name>Jessica Arnold</Name>
<Name>Jessica Arnold</Name>
```

<span data-ttu-id="e2443-111">Bu, eksenin uygulamalarından biri `Elements` üzerinde bir genişletme yöntemi olduğu için geçerlidir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="e2443-111">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="e2443-112"><xref:System.Xml.Linq.XElement> ' dan türetilir <xref:System.Xml.Linq.XContainer> , bu sayede yöntemine yapılan <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> çağrının sonuçlarında yöntemi çağırabilirsiniz <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e2443-112"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>

## <a name="example-retrieve-all-elements-at-a-particular-depth"></a><span data-ttu-id="e2443-113">Örnek: tüm öğeleri belirli bir derinlikte al</span><span class="sxs-lookup"><span data-stu-id="e2443-113">Example: Retrieve all elements at a particular depth</span></span>

<span data-ttu-id="e2443-114">Bazı durumlarda, aradaki üst öğeler olmadığında, belirli bir öğe derinliğinde tüm öğeleri almak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="e2443-114">Sometimes you want to retrieve all elements at a particular element depth when there may not be intervening ancestors.</span></span> <span data-ttu-id="e2443-115">Örneğin, aşağıdaki belgede, öğesinin alt öğesi olan tüm öğeleri almak isteyebilirsiniz `ConfigParameter` `Customer` , ancak `ConfigParameter` öğenin bir alt öğesi olamaz `Root` .</span><span class="sxs-lookup"><span data-stu-id="e2443-115">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that's a child of the `Root` element.</span></span>

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

 <span data-ttu-id="e2443-116">Bunu yapmak için, <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> aşağıdaki gibi, eksenini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e2443-116">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>

```csharp
XElement root = XElement.Load("Irregular.xml");
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").
    Elements("ConfigParameter");
foreach (XElement cp in configParameters)
    Console.WriteLine(cp);
```

```vb
Dim root As XElement = XElement.Load("Irregular.xml")
Dim configParameters As IEnumerable(Of XElement) = _
    root.<Customer>.<Config>.<ConfigParameter>
For Each cp As XElement In configParameters
    Console.WriteLine(cp)
Next
```

<span data-ttu-id="e2443-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e2443-117">This example produces the following output:</span></span>

```xml
<ConfigParameter>FirstConfigParameter</ConfigParameter>
<ConfigParameter>SecondConfigParameter</ConfigParameter>
```

## <a name="example-retrieve-elements-for-xml-thats-in-a-namespace"></a><span data-ttu-id="e2443-118">Örnek: bir ad alanında bulunan XML için öğeleri alma</span><span class="sxs-lookup"><span data-stu-id="e2443-118">Example: Retrieve elements for XML that's in a namespace</span></span>

<span data-ttu-id="e2443-119">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı tekniği gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2443-119">The following example shows the same technique for XML that's in a namespace.</span></span> <span data-ttu-id="e2443-120">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2443-120">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="e2443-121">Bu örnek, XML belgesi [örnek xml dosyası kullanır: bir ad alanında birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e2443-121">This example uses XML document [Sample XML file: Multiple purchase orders in a namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span></span>

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

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim names As IEnumerable(Of XElement) = _
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _
            Select el
        For Each e As XElement In names
            Console.WriteLine(e)
        Next
    End Sub
End Module
```

<span data-ttu-id="e2443-122">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e2443-122">This example produces the following output:</span></span>

```xml
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
```

## <a name="see-also"></a><span data-ttu-id="e2443-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2443-123">See also</span></span>

- [<span data-ttu-id="e2443-124">LINQ to XML eksenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="e2443-124">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
