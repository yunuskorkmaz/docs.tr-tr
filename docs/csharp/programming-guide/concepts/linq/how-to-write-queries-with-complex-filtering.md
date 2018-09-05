---
title: 'Nasıl yapılır: karmaşık (C#) filtreleme ile sorgu yazma'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 2f8eef2f75e45212b3493aa1b6f813c52beb7665
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508839"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="dd1b1-102">Nasıl yapılır: karmaşık (C#) filtreleme ile sorgu yazma</span><span class="sxs-lookup"><span data-stu-id="dd1b1-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="dd1b1-103">Bazen karmaşık filtrelerle XML sorgularında LINQ yazmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="dd1b1-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="dd1b1-104">Örneğin, bir özel ad ve değer olan bir alt öğesi olan tüm öğeleri Bul gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="dd1b1-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="dd1b1-105">Bu konu, karmaşık filtreleme ile sorgu yazma örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd1b1-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd1b1-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd1b1-106">Example</span></span>  
 <span data-ttu-id="dd1b1-107">Bu örnekte tüm bulmayı gösteren `PurchaseOrder` alt olan öğeler `Address` sahip öğe bir `Type` özniteliği "Gönderim" hem de bir alt gruba eşit `State` öğesi "NY için" eşit.</span><span class="sxs-lookup"><span data-stu-id="dd1b1-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="dd1b1-108">İç içe bir sorgu kullanan `Where` yan tümcesi ve `Any` işleci döndürür `true` koleksiyonu herhangi bir öğe varsa.</span><span class="sxs-lookup"><span data-stu-id="dd1b1-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="dd1b1-109">Metot tabanlı sorgu söz dizimi hakkında daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="dd1b1-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="dd1b1-110">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: birden fazla satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dd1b1-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="dd1b1-111">Hakkında daha fazla bilgi için `Any` işleci bkz [Niceleyici işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="dd1b1-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="dd1b1-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="dd1b1-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="dd1b1-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd1b1-113">Example</span></span>  
 <span data-ttu-id="dd1b1-114">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd1b1-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="dd1b1-115">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="dd1b1-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="dd1b1-116">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: bir Namespace, birden fazla satın alma siparişi](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="dd1b1-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="dd1b1-117">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="dd1b1-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd1b1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd1b1-118">See Also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
- [<span data-ttu-id="dd1b1-119">Temel sorgular (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="dd1b1-119">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
- [<span data-ttu-id="dd1b1-120">Projeksiyon işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="dd1b1-120">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
- [<span data-ttu-id="dd1b1-121">Niceleyici işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="dd1b1-121">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
