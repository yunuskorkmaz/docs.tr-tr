---
title: Karmaşık filtreleme (C#) ile sorgu yazma
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: bc85d7f1e5c5305407ad22f3ada908523313d964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168524"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="b07ff-102">Karmaşık filtreleme (C#) ile sorgu yazma</span><span class="sxs-lookup"><span data-stu-id="b07ff-102">How to write queries with complex filtering (C#)</span></span>
<span data-ttu-id="b07ff-103">Bazen karmaşık filtrelerle XML sorgularına LINQ yazmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b07ff-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="b07ff-104">Örneğin, belirli bir ada ve değere sahip bir alt öğeye sahip tüm öğeleri bulmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b07ff-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="b07ff-105">Bu konu karmaşık filtreleme ile bir sorgu yazma bir örnek verir.</span><span class="sxs-lookup"><span data-stu-id="b07ff-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b07ff-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b07ff-106">Example</span></span>  
 <span data-ttu-id="b07ff-107">Bu örnek, "Gönderim" ile `PurchaseOrder` `Address` eşit bir `Type` özniteliği olan bir alt öğeye `State` sahip tüm öğeleri ve "NY" ile eşit bir alt öğeyi nasıl bulabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b07ff-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="b07ff-108">Yan tümcede iç içe bir `Any` sorgu kullanır ve koleksiyonda herhangi bir öğe varsa işleç döndürür. `true` `Where`</span><span class="sxs-lookup"><span data-stu-id="b07ff-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="b07ff-109">Yöntem tabanlı sorgu sözdizimini kullanma hakkında bilgi [için, LINQ'da Sorgu Sözdizimi ve Yöntem Sözdizimi'ne](./query-syntax-and-method-syntax-in-linq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b07ff-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="b07ff-110">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Birden Çok SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b07ff-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b07ff-111">`Any` Operatör hakkında daha fazla bilgi için [Quantifier Operations (C#)](./quantifier-operations.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b07ff-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="b07ff-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b07ff-112">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="b07ff-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b07ff-113">Example</span></span>  
 <span data-ttu-id="b07ff-114">Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b07ff-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="b07ff-115">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b07ff-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b07ff-116">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında birden çok Satınalma Siparişi.](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md)</span><span class="sxs-lookup"><span data-stu-id="b07ff-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="b07ff-117">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b07ff-117">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="b07ff-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b07ff-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="b07ff-119">Projeksiyon İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b07ff-119">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="b07ff-120">Niceleyici İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b07ff-120">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
