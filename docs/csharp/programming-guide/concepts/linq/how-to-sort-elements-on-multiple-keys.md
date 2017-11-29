---
title: "Nasıl yapılır: sıralama öğeleri birden çok anahtarlar (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3b2760b6-d607-4ac7-b784-5c6524e2a0e0
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5ec1873ce9d7c6a3c791597eaab48071be44a997
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-sort-elements-on-multiple-keys-c"></a><span data-ttu-id="56dab-102">Nasıl yapılır: sıralama öğeleri birden çok anahtarlar (C#)</span><span class="sxs-lookup"><span data-stu-id="56dab-102">How to: Sort Elements on Multiple Keys (C#)</span></span>
<span data-ttu-id="56dab-103">Bu konu, üzerinde birden çok anahtar sıralama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="56dab-103">This topic shows how to sort on multiple keys.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56dab-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="56dab-104">Example</span></span>  
 <span data-ttu-id="56dab-105">Bu örnekte, sonuçları ilk sevkiyat posta kodu tarafından sonra sipariş tarihine göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="56dab-105">In this example, the results are ordered first by the shipping postal code, then by the order date.</span></span>  
  
 <span data-ttu-id="56dab-106">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="56dab-106">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
var sortedElements =  
    from c in co.Element("Orders").Elements("Order")  
    orderby (string)c.Element("ShipInfo").Element("ShipPostalCode"),  
            (DateTime)c.Element("OrderDate")  
    select new {  
        CustomerID = (string)c.Element("CustomerID"),  
        EmployeeID = (string)c.Element("EmployeeID"),  
        ShipPostalCode = (string)c.Element("ShipInfo").Element("ShipPostalCode"),  
        OrderDate = (DateTime)c.Element("OrderDate")  
    };  
foreach (var r in sortedElements)  
    Console.WriteLine("CustomerID:{0} EmployeeID:{1} ShipPostalCode:{2} OrderDate:{3:d}",  
        r.CustomerID, r.EmployeeID, r.ShipPostalCode, r.OrderDate);  
```  
  
 <span data-ttu-id="56dab-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="56dab-107">This code produces the following output:</span></span>  
  
```  
CustomerID:LETSS EmployeeID:1 ShipPostalCode:94117 OrderDate:6/25/1997  
CustomerID:LETSS EmployeeID:8 ShipPostalCode:94117 OrderDate:10/27/1997  
CustomerID:LETSS EmployeeID:6 ShipPostalCode:94117 OrderDate:11/10/1997  
CustomerID:LETSS EmployeeID:4 ShipPostalCode:94117 OrderDate:2/12/1998  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:5/6/1997  
CustomerID:GREAL EmployeeID:8 ShipPostalCode:97403 OrderDate:7/4/1997  
CustomerID:GREAL EmployeeID:1 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:9/4/1997  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:9/25/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:1/6/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:3/9/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:4/7/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/22/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/30/1998  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:12/6/1996  
CustomerID:HUNGC EmployeeID:1 ShipPostalCode:97827 OrderDate:12/25/1996  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:1/15/1997  
CustomerID:HUNGC EmployeeID:4 ShipPostalCode:97827 OrderDate:7/16/1997  
CustomerID:HUNGC EmployeeID:8 ShipPostalCode:97827 OrderDate:9/8/1997  
CustomerID:LAZYK EmployeeID:1 ShipPostalCode:99362 OrderDate:3/21/1997  
CustomerID:LAZYK EmployeeID:8 ShipPostalCode:99362 OrderDate:5/22/1997  
```  
  
## <a name="example"></a><span data-ttu-id="56dab-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="56dab-108">Example</span></span>  
 <span data-ttu-id="56dab-109">Aşağıdaki örnek bir ad alanı XML aynı sorgu gösterir.</span><span class="sxs-lookup"><span data-stu-id="56dab-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="56dab-110">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="56dab-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="56dab-111">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve bir Namespace siparişler](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="56dab-111">This example uses the following XML document: [Sample XML File: Customers and Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
var sortedElements =  
    from c in co.Element(aw + "Orders").Elements(aw + "Order")  
    orderby (string)c.Element(aw + "ShipInfo").Element(aw + "ShipPostalCode"),  
            (DateTime)c.Element(aw + "OrderDate")  
    select new  
    {  
        CustomerID = (string)c.Element(aw + "CustomerID"),  
        EmployeeID = (string)c.Element(aw + "EmployeeID"),  
        ShipPostalCode = (string)c.Element(aw + "ShipInfo").Element(aw + "ShipPostalCode"),  
        OrderDate = (DateTime)c.Element(aw + "OrderDate")  
    };  
foreach (var r in sortedElements)  
    Console.WriteLine("CustomerID:{0} EmployeeID:{1} ShipPostalCode:{2} OrderDate:{3:d}",  
        r.CustomerID, r.EmployeeID, r.ShipPostalCode, r.OrderDate);  
```  
  
 <span data-ttu-id="56dab-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="56dab-112">This code produces the following output:</span></span>  
  
```  
CustomerID:LETSS EmployeeID:1 ShipPostalCode:94117 OrderDate:6/25/1997  
CustomerID:LETSS EmployeeID:8 ShipPostalCode:94117 OrderDate:10/27/1997  
CustomerID:LETSS EmployeeID:6 ShipPostalCode:94117 OrderDate:11/10/1997  
CustomerID:LETSS EmployeeID:4 ShipPostalCode:94117 OrderDate:2/12/1998  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:5/6/1997  
CustomerID:GREAL EmployeeID:8 ShipPostalCode:97403 OrderDate:7/4/1997  
CustomerID:GREAL EmployeeID:1 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:9/4/1997  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:9/25/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:1/6/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:3/9/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:4/7/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/22/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/30/1998  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:12/6/1996  
CustomerID:HUNGC EmployeeID:1 ShipPostalCode:97827 OrderDate:12/25/1996  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:1/15/1997  
CustomerID:HUNGC EmployeeID:4 ShipPostalCode:97827 OrderDate:7/16/1997  
CustomerID:HUNGC EmployeeID:8 ShipPostalCode:97827 OrderDate:9/8/1997  
CustomerID:LAZYK EmployeeID:1 ShipPostalCode:99362 OrderDate:3/21/1997  
CustomerID:LAZYK EmployeeID:8 ShipPostalCode:99362 OrderDate:5/22/1997  
```  
  
## <a name="see-also"></a><span data-ttu-id="56dab-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56dab-113">See Also</span></span>  
 [<span data-ttu-id="56dab-114">Temel sorgu (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="56dab-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
