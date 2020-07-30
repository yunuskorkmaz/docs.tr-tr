---
title: Karmaşık filtrelemeye sahip sorguları yazma (C#)
description: Karmaşık filtrelerle LINQ to XML sorguları yazmayı öğrenin. Kod örneklerine bakın ve ek kaynakları görüntüleyin.
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 5d2c1aafc210b35d4d6b1f1b2d74b11966d90c80
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303432"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="e4928-104">Karmaşık filtrelemeye sahip sorguları yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="e4928-104">How to write queries with complex filtering (C#)</span></span>
<span data-ttu-id="e4928-105">Bazen karmaşık filtrelerle LINQ to XML sorguları yazmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4928-105">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="e4928-106">Örneğin, belirli bir ada ve değere sahip bir alt öğesi olan tüm öğeleri bulmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e4928-106">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="e4928-107">Bu konu, karmaşık filtrelemeye sahip sorgu yazma örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4928-107">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4928-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4928-108">Example</span></span>  
 <span data-ttu-id="e4928-109">Bu örnek `PurchaseOrder` `Address` , bir `Type` özniteliği "Shipping" ve alt `State` öğesi "NY" değerine eşit olan bir alt öğesi olan tüm öğelerin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4928-109">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="e4928-110">Yan tümcesinde iç içe geçmiş bir sorgu kullanır `Where` ve `Any` koleksiyonda herhangi bir öğe varsa işleç döndürülür `true` .</span><span class="sxs-lookup"><span data-stu-id="e4928-110">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="e4928-111">Yöntem tabanlı sorgu söz dizimini kullanma hakkında daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="e4928-111">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="e4928-112">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: birden fazla satın alma siparişi (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e4928-112">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e4928-113">İşleci hakkında daha fazla bilgi için `Any` bkz. [nicelik belirteci Işlemleri (C#)](./quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e4928-113">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="e4928-114">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e4928-114">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="e4928-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4928-115">Example</span></span>  
 <span data-ttu-id="e4928-116">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4928-116">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e4928-117">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e4928-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e4928-118">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında birden fazla satın alma siparişi](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e4928-118">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="e4928-119">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e4928-119">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4928-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4928-120">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="e4928-121">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="e4928-121">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="e4928-122">Nicelik belirteci Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="e4928-122">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
