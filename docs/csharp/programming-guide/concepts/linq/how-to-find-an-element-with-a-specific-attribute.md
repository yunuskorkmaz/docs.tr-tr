---
title: Belirli bir özniteliğe sahip bir öğe bulma (C#)
description: Belirli bir değere sahip bir özniteliğe sahip bir öğe bulmayı öğrenin. Kod örneklerine ve ek kaynaklara bakın.
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 44875ca2104e7a8f83e83da983af49ef85c89f0a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303289"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="e2dfd-104">Belirli bir özniteliğe sahip bir öğe bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-104">How to find an element with a specific attribute (C#)</span></span>
<span data-ttu-id="e2dfd-105">Bu konu, belirli bir değere sahip bir özniteliğe sahip olan bir öğenin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-105">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2dfd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2dfd-106">Example</span></span>  
 <span data-ttu-id="e2dfd-107">Örnek, `Address` `Type` "Faturalandırma" değerine sahip bir özniteliğe sahip olan öğenin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-107">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="e2dfd-108">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="e2dfd-108">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e2dfd-109">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e2dfd-109">This code produces the following output:</span></span>  
  
```xml  
<Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="example"></a><span data-ttu-id="e2dfd-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2dfd-110">Example</span></span>  
 <span data-ttu-id="e2dfd-111">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e2dfd-112">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e2dfd-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e2dfd-113">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında tipik satın alma siparişi](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e2dfd-113">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> address =  
    from el in root.Elements(aw + "Address")  
    where (string)el.Attribute(aw + "Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e2dfd-114">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e2dfd-114">This code produces the following output:</span></span>  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2dfd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="e2dfd-116">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-116">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="e2dfd-117">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-117">Projection Operations (C#)</span></span>](./projection-operations.md)
