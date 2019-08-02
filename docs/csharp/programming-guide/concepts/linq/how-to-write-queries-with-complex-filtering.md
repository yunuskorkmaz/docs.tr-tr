---
title: 'Nasıl yapılır: Karmaşık filtrelemeye (C#) sahip sorguları yazma'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 08c1e124542e6d7e4c728102b2aa7fb4a804794c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710036"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="d7a68-102">Nasıl yapılır: Karmaşık filtrelemeye (C#) sahip sorguları yazma</span><span class="sxs-lookup"><span data-stu-id="d7a68-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="d7a68-103">Bazen karmaşık filtrelerle LINQ to XML sorguları yazmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7a68-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="d7a68-104">Örneğin, belirli bir ada ve değere sahip bir alt öğesi olan tüm öğeleri bulmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d7a68-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="d7a68-105">Bu konu, karmaşık filtrelemeye sahip sorgu yazma örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7a68-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7a68-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7a68-106">Example</span></span>  
 <span data-ttu-id="d7a68-107">Bu `PurchaseOrder` örnek, `Address` `State` bir özniteliği "Shipping" ve alt öğesi "NY" değerine eşit olan bir alt öğesi olan tüm öğelerin nasıl bulunacağını gösterir. `Type`</span><span class="sxs-lookup"><span data-stu-id="d7a68-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="d7a68-108">`Where` Yan tümcesinde iç içe geçmiş bir sorgu kullanır `Any` ve koleksiyonda herhangi bir öğe `true` varsa işleç döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d7a68-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="d7a68-109">Yöntem tabanlı sorgu söz dizimini kullanma hakkında daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="d7a68-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="d7a68-110">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Birden çok satın alma siparişi (](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="d7a68-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d7a68-111">`Any` İşleci hakkında daha fazla bilgi için bkz. [nicelik belirteci işlemleriC#()](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d7a68-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="d7a68-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d7a68-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="d7a68-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7a68-113">Example</span></span>  
 <span data-ttu-id="d7a68-114">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7a68-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d7a68-115">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d7a68-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d7a68-116">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Bir ad alanında](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)birden fazla satın alma siparişi.</span><span class="sxs-lookup"><span data-stu-id="d7a68-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="d7a68-117">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d7a68-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7a68-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7a68-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="d7a68-119">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="d7a68-119">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="d7a68-120">Nicelik belirteci IşlemleriC#()</span><span class="sxs-lookup"><span data-stu-id="d7a68-120">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
