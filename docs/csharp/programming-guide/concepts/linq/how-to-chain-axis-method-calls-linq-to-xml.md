---
title: 'Nasıl yapılır: zincir eksen yöntem çağrıları (LINQ-XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 36160a9dd4cc26b0b1d54e6e8b91d2880dd23abf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333784"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="9d436-102">Nasıl yapılır: zincir eksen yöntem çağrıları (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9d436-102">How to: Chain Axis Method Calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9d436-103">Kodunuzda kullanacağınız genel bir desen bir eksen yöntemini çağırın, ardından çağrısı uzantısı yöntemi eksenleri birini ' dir.</span><span class="sxs-lookup"><span data-stu-id="9d436-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="9d436-104">İki eksen adı vardır `Elements` öğe koleksiyonunu döndürür: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yöntemi ve <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9d436-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9d436-105">Belirtilen adın tüm öğeleri verilen derinliğinde ağacında bulmak için bu iki eksenler birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d436-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d436-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d436-106">Example</span></span>  
 <span data-ttu-id="9d436-107">Bu örnekte <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> ve <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> tüm bulmak için `Name` tüm öğeleri `Address` tüm öğeleri `PurchaseOrder` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9d436-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="9d436-108">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: birden çok satınalma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9d436-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9d436-109">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="9d436-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="9d436-110">Bu çalışır çünkü uygulamaları birini `Elements` ekseni üzerinde bir genişletme yöntemi değil <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="9d436-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="9d436-111"><xref:System.Xml.Linq.XElement> türetilen <xref:System.Xml.Linq.XContainer>, çağırabilirsiniz <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrı sonuçları <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9d436-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d436-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d436-112">Example</span></span>  
 <span data-ttu-id="9d436-113">Bazen belirli öğesinin derinliği tüm öğeler almak istediğiniz zaman var olabilir veya araya giren üst öğelerinden olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9d436-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="9d436-114">Örneğin, aşağıdaki belgede, tüm almak isteyebilirsiniz `ConfigParameter` , alt öğelerini `Customer` öğesi, ama `ConfigParameter` olan bir alt `Root` öğesi.</span><span class="sxs-lookup"><span data-stu-id="9d436-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="9d436-115">Bunu yapmak için kullanabileceğiniz <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> şekilde eksen:</span><span class="sxs-lookup"><span data-stu-id="9d436-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="9d436-116">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="9d436-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="9d436-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d436-117">Example</span></span>  
 <span data-ttu-id="9d436-118">Aşağıdaki örnek, bir ad alanı içinde XML için aynı yöntemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d436-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="9d436-119">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="9d436-119">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="9d436-120">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: bir Namespace içinde birden çok satınalma siparişi](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="9d436-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="9d436-121">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="9d436-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d436-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d436-122">See Also</span></span>  
 [<span data-ttu-id="9d436-123">LINQ-XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="9d436-123">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
