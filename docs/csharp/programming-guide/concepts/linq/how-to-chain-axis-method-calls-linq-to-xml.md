---
title: Eksen yöntemi çağrıları (LINQ- XML) (C#) nasıl zincirilir?
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 56fa5c9e8358883d838b68e99664240aa97f347f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169473"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="4ac1e-102">Eksen yöntemi çağrıları (LINQ- XML) (C#) nasıl zincirilir?</span><span class="sxs-lookup"><span data-stu-id="4ac1e-102">How to chain axis method calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4ac1e-103">Kodunuzda kullanacağınız yaygın bir desen, eksen yöntemini çağırmak, ardından uzantı yöntemi eksenlerinden birini çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="4ac1e-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="4ac1e-104">Bu döndürme öğeleri bir `Elements` koleksiyon adı ile iki <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> eksen <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> vardır: yöntem ve yöntem.</span><span class="sxs-lookup"><span data-stu-id="4ac1e-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4ac1e-105">Ağaçta belirli bir derinlikte belirli bir adın tüm öğelerini bulmak için bu iki ekseni birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ac1e-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ac1e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ac1e-106">Example</span></span>  
 <span data-ttu-id="4ac1e-107"><xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> Bu örnek, <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> tüm `Name` `Address` `PurchaseOrder` öğelerdeki tüm öğelerdeki tüm öğeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ac1e-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="4ac1e-108">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Birden Çok SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4ac1e-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="4ac1e-109">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4ac1e-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="4ac1e-110">`Elements` Eksenin uygulamalarından biri üzerinde <xref:System.Collections.Generic.IEnumerable%601> bir uzantı yöntemi olarak olduğu için bu <xref:System.Xml.Linq.XContainer>çalışır.</span><span class="sxs-lookup"><span data-stu-id="4ac1e-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="4ac1e-111"><xref:System.Xml.Linq.XElement><xref:System.Xml.Linq.XContainer>türetilmiştir, böylece <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yönteme yapılan bir çağrının sonuçlarında metodu arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ac1e-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ac1e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ac1e-112">Example</span></span>  
 <span data-ttu-id="4ac1e-113">Bazen, müdahale eden atalar olabilir veya olmayabilir belirli bir öğe derinliğinde tüm öğeleri almak istiyorum.</span><span class="sxs-lookup"><span data-stu-id="4ac1e-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="4ac1e-114">Örneğin, aşağıdaki `ConfigParameter` belgede, `Customer` öğenin alt öğeleri olan tüm öğeleri almak isteyebilirsiniz, `ConfigParameter` ancak `Root` öğenin bir alt değil.</span><span class="sxs-lookup"><span data-stu-id="4ac1e-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="4ac1e-115">Bunu yapmak için ekseni <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> aşağıdaki gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4ac1e-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="4ac1e-116">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4ac1e-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="4ac1e-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ac1e-117">Example</span></span>  
 <span data-ttu-id="4ac1e-118">Aşağıdaki örnek, xml için bir ad alanında olan aynı tekniği gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ac1e-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="4ac1e-119">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4ac1e-119">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="4ac1e-120">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında birden çok Satınalma Siparişi.](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md)</span><span class="sxs-lookup"><span data-stu-id="4ac1e-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="4ac1e-121">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4ac1e-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ac1e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ac1e-122">See also</span></span>

- [<span data-ttu-id="4ac1e-123">LINQ - XML Eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="4ac1e-123">LINQ to XML Axes (C#)</span></span>](linq-to-xml-axes-overview.md)
