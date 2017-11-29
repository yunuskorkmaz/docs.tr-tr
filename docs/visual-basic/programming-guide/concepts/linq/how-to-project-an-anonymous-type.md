---
title: "Nasıl yapılır: Proje anonim bir türü (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b383b0a7e0fc0aa22bdcc8ed87628947858986da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="e4b20-102">Nasıl yapılır: Proje anonim bir türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4b20-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="e4b20-103">Bazı durumlarda, yalnızca kısa bir süre bu tür kullanacağınız bilseniz bile bir sorgu yeni bir tür için proje isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4b20-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="e4b20-104">Yalnızca yansıtma kullanmak için yeni bir türü oluşturmak için ek iş çok karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="e4b20-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="e4b20-105">Daha verimli bir yaklaşım için bu durumda olan anonim bir tür projeye.</span><span class="sxs-lookup"><span data-stu-id="e4b20-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="e4b20-106">Anonim türler, bir sınıf tanımlama sonra bildirme ve bu sınıfın bir nesnesi sınıfı bir ad verip olmadan başlatma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e4b20-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="e4b20-107">Anonim türler matematiksel kavramı, C# uygulaması olan bir *tanımlama grubu*.</span><span class="sxs-lookup"><span data-stu-id="e4b20-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="e4b20-108">Matematik terim tanımlama grubu tek dizisinden çift kaynaklanan Üçlü, dört, beş kez, n-tanımlama grubu.</span><span class="sxs-lookup"><span data-stu-id="e4b20-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="e4b20-109">Sınırlı dizisi nesneleri için belirli bir türdeki her başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="e4b20-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="e4b20-110">Bazen bu ad/değer çiftlerinin listesini denir.</span><span class="sxs-lookup"><span data-stu-id="e4b20-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="e4b20-111">Örneğin, bir adres içeriğini [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML belgesi ifade edilir şekilde:</span><span class="sxs-lookup"><span data-stu-id="e4b20-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="e4b20-112">Anonim bir türün bir örneği oluşturduğunuzda, bunu sipariş n tanımlama grubu oluşturma olarak düşünün uygundur.</span><span class="sxs-lookup"><span data-stu-id="e4b20-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="e4b20-113">İçinde bir tanımlama grubu oluşturur bir sorgu yazın, `Select` yan tümcesi, sorgunun döndürdüğü bir `IEnumerable` kayıt.</span><span class="sxs-lookup"><span data-stu-id="e4b20-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4b20-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4b20-114">Example</span></span>  
 <span data-ttu-id="e4b20-115">Bu örnekte, `Select` yan tümcesi projeleri anonim bir tür.</span><span class="sxs-lookup"><span data-stu-id="e4b20-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="e4b20-116">Bu örnek daha sonra kullanır `Dim` oluşturmak için `IEnumerable` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e4b20-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="e4b20-117">İçinde `For Each` döngü, yineleme değişkeni sorgu ifadesinde oluşturulan anonim türünün bir örneği haline gelir.</span><span class="sxs-lookup"><span data-stu-id="e4b20-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="e4b20-118">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e4b20-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 <span data-ttu-id="e4b20-119">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e4b20-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4b20-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4b20-120">See Also</span></span>  
 [<span data-ttu-id="e4b20-121">Projeksiyonlar ve dönüştürmeler (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4b20-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
