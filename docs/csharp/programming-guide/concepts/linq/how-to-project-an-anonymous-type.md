---
title: 'Nasıl yapılır: Proje anonim bir tür (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 6ecb29c59d16b64b1dfb7018a2d22ae81242ee81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320683"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="24fb5-102">Nasıl yapılır: Proje anonim bir tür (C#)</span><span class="sxs-lookup"><span data-stu-id="24fb5-102">How to: Project an Anonymous Type (C#)</span></span>
<span data-ttu-id="24fb5-103">Bazı durumlarda, yalnızca kısa bir süre bu tür kullanacağınız bilseniz bile bir sorgu yeni bir tür için proje isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24fb5-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="24fb5-104">Yalnızca yansıtma kullanmak için yeni bir türü oluşturmak için ek iş çok karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="24fb5-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="24fb5-105">Daha verimli bir yaklaşım için bu durumda olan anonim bir tür projeye.</span><span class="sxs-lookup"><span data-stu-id="24fb5-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="24fb5-106">Anonim türler, bir sınıf tanımlama sonra bildirme ve bu sınıfın bir nesnesi sınıfı bir ad verip olmadan başlatma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="24fb5-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="24fb5-107">Anonim türler matematiksel kavramı, C# uygulaması olan bir *tanımlama grubu*.</span><span class="sxs-lookup"><span data-stu-id="24fb5-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="24fb5-108">Matematik terim tanımlama grubu tek dizisinden çift kaynaklanan Üçlü, dört, beş kez, n-tanımlama grubu.</span><span class="sxs-lookup"><span data-stu-id="24fb5-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="24fb5-109">Sınırlı dizisi nesneleri için belirli bir türdeki her başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="24fb5-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="24fb5-110">Bazen bu ad/değer çiftlerinin listesini denir.</span><span class="sxs-lookup"><span data-stu-id="24fb5-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="24fb5-111">Örneğin, bir adres içeriğini [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML belgesi ifade edilir şekilde:</span><span class="sxs-lookup"><span data-stu-id="24fb5-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="24fb5-112">Anonim bir türün bir örneği oluşturduğunuzda, bunu sipariş n tanımlama grubu oluşturma olarak düşünün uygundur.</span><span class="sxs-lookup"><span data-stu-id="24fb5-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="24fb5-113">İçinde bir tanımlama grubu oluşturur bir sorgu yazın, `select` yan tümcesi, sorgunun döndürdüğü bir `IEnumerable` kayıt.</span><span class="sxs-lookup"><span data-stu-id="24fb5-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24fb5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="24fb5-114">Example</span></span>  
 <span data-ttu-id="24fb5-115">Bu örnekte, `select` yan tümcesi projeleri anonim bir tür.</span><span class="sxs-lookup"><span data-stu-id="24fb5-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="24fb5-116">Bu örnek daha sonra kullanır `var` oluşturmak için `IEnumerable` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="24fb5-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="24fb5-117">İçinde `foreach` döngü, yineleme değişkeni sorgu ifadesinde oluşturulan anonim türünün bir örneği haline gelir.</span><span class="sxs-lookup"><span data-stu-id="24fb5-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="24fb5-118">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="24fb5-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 <span data-ttu-id="24fb5-119">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="24fb5-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="24fb5-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24fb5-120">See Also</span></span>  
 [<span data-ttu-id="24fb5-121">Projeksiyonlar ve dönüştürmeler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="24fb5-121">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
