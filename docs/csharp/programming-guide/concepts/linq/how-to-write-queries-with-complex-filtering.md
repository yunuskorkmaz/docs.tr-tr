---
title: "Nasıl yapılır: karmaşık (C#) filtreleme ile sorguları yazma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0d663b777b0d1b02462a6557097938831ef870b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="b252e-102">Nasıl yapılır: karmaşık (C#) filtreleme ile sorguları yazma</span><span class="sxs-lookup"><span data-stu-id="b252e-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="b252e-103">Bazen LINQ XML sorguları karmaşık filtrelerle yazmak istiyorum.</span><span class="sxs-lookup"><span data-stu-id="b252e-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="b252e-104">Örneğin, bir özel ad ve değer olan bir alt öğesi olan tüm öğeleri bulmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="b252e-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="b252e-105">Bu konuda, karmaşık filtreleme ile bir sorgu yazma bir örnek verir.</span><span class="sxs-lookup"><span data-stu-id="b252e-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b252e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b252e-106">Example</span></span>  
 <span data-ttu-id="b252e-107">Bu örnekte tüm bulmayı gösteren `PurchaseOrder` olan bir alt öğenin `Address` sahip öğe bir `Type` özniteliği "Aktarma" ve bir alt eşit `State` öğesi "NY" eşit.</span><span class="sxs-lookup"><span data-stu-id="b252e-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="b252e-108">İç içe bir sorgu kullanır `Where` yan tümcesi ve `Any` operatörü döndürür `true` koleksiyonu herhangi bir öğe varsa.</span><span class="sxs-lookup"><span data-stu-id="b252e-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="b252e-109">Yöntem temelli sorgu sözdizimini kullanma hakkında daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="b252e-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="b252e-110">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: birden çok satınalma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b252e-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b252e-111">Hakkında daha fazla bilgi için `Any` işleci, bkz: [Niceleyici işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b252e-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="b252e-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b252e-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="b252e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b252e-113">Example</span></span>  
 <span data-ttu-id="b252e-114">Aşağıdaki örnek bir ad alanı XML aynı sorgu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b252e-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="b252e-115">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b252e-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="b252e-116">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: bir Namespace içinde birden çok satınalma siparişi](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b252e-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="b252e-117">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b252e-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="b252e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b252e-118">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="b252e-119">Temel sorgu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b252e-119">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="b252e-120">Projeksiyon işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b252e-120">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
 [<span data-ttu-id="b252e-121">Niceleyici işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b252e-121">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
