---
title: 'Nasıl yapılır: Anonim tip yansıtma (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: d19fd40b213280523d0d731e5e3e8ba5213bcd49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701846"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="c9c5a-102">Nasıl yapılır: Anonim tip yansıtma (C#)</span><span class="sxs-lookup"><span data-stu-id="c9c5a-102">How to: Project an Anonymous Type (C#)</span></span>
<span data-ttu-id="c9c5a-103">Bazı durumlarda bu tür yalnızca kısa bir süre için kullanacağı bilseniz bile bir sorgu yeni bir tür için proje isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="c9c5a-104">Bu, birçok yalnızca projeksiyonda kullanmak için yeni bir tür oluşturmak için fazladan iş olur.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="c9c5a-105">Daha verimli bir yaklaşım için bu durumda, anonim bir tür için proje.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="c9c5a-106">Anonim türler bir sınıf tanımlama sonra bildirir ve sınıfı bir ad vererek olmadan söz konusu sınıfın bir nesnesi başlatılmaya olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="c9c5a-107">Anonim türler matematik kavramı, C# uygulaması bir *demet*.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="c9c5a-108">Matematik terimi demet tek dizisinden çift kaynaklanan üç, dört, beş kez, n-tanımlama grubu.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="c9c5a-109">Bu sınırlı dizisi ile nesneleri belirli bir türdeki her ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="c9c5a-110">Bazen bu ad/değer çiftlerinin listesini denir.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="c9c5a-111">Örneğin, bir adres içeriğini [örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML belgesi ifade edilemez gibi:</span><span class="sxs-lookup"><span data-stu-id="c9c5a-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="c9c5a-112">Anonim bir türün örneğini oluşturduğunuzda, bunu order n tanımlama grubu oluşturma olarak düşünün kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="c9c5a-113">Bir grup içinde oluşturan bir sorgu yazma, `select` sorgu yan tümcesi döndürür bir `IEnumerable` düzeninin.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9c5a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9c5a-114">Example</span></span>  
 <span data-ttu-id="c9c5a-115">Bu örnekte, `select` yan tümcesi projeleri anonim bir tür.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="c9c5a-116">Ardından örnekte `var` oluşturmak için `IEnumerable` nesne.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="c9c5a-117">İçinde `foreach` döngüsünün yineleme değişkeni sorgu ifadesi içinde oluşturulan anonim türün bir örneğini haline gelir.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="c9c5a-118">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="c9c5a-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="c9c5a-119">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c9c5a-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9c5a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9c5a-120">See also</span></span>

- [<span data-ttu-id="c9c5a-121">Projeksiyonlar ve Dönüşümler (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c9c5a-121">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
