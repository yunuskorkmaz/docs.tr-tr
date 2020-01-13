---
title: Karmaşık filtrelemeye (C#) sahip sorguları yazma
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: a4918631fed21967b402c5c56cfb8a211d44c139
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337356"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="0f90f-102">Karmaşık filtrelemeye (C#) sahip sorguları yazma</span><span class="sxs-lookup"><span data-stu-id="0f90f-102">How to write queries with complex filtering (C#)</span></span>
<span data-ttu-id="0f90f-103">Bazen karmaşık filtrelerle LINQ to XML sorguları yazmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f90f-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="0f90f-104">Örneğin, belirli bir ada ve değere sahip bir alt öğesi olan tüm öğeleri bulmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0f90f-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="0f90f-105">Bu konu, karmaşık filtrelemeye sahip sorgu yazma örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f90f-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f90f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f90f-106">Example</span></span>  
 <span data-ttu-id="0f90f-107">Bu örnek, bir `Type` özniteliği "Shipping" ve bir alt `State` öğesi "NY" değerine eşit olan bir alt `Address` öğesi olan tüm `PurchaseOrder` öğelerinin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f90f-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="0f90f-108">`Where` yan tümcesinde iç içe geçmiş bir sorgu kullanır ve koleksiyonda herhangi bir öğe varsa `Any` işleci `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f90f-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="0f90f-109">Yöntem tabanlı sorgu söz dizimini kullanma hakkında daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="0f90f-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="0f90f-110">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: birden fazla satın alma siparişi (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0f90f-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0f90f-111">`Any` işleci hakkında daha fazla bilgi için bkz. [nicelik belirteci işlemleriC#()](./quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0f90f-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="0f90f-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0f90f-112">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="0f90f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f90f-113">Example</span></span>  
 <span data-ttu-id="0f90f-114">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f90f-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="0f90f-115">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0f90f-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0f90f-116">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında birden fazla satın alma siparişi](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="0f90f-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="0f90f-117">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0f90f-117">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f90f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f90f-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="0f90f-119">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="0f90f-119">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="0f90f-120">Nicelik belirteci IşlemleriC#()</span><span class="sxs-lookup"><span data-stu-id="0f90f-120">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
