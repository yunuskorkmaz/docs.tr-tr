---
title: 'Nasıl yapılır: Anonim Tip Yansıtma'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: c486fbd7ee8ae917cd0ccf57e2b04e472784b11d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810566"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="aec90-102">Nasıl yapılır: anonim bir tür proje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aec90-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="aec90-103">Bazı durumlarda, bu türü yalnızca kısa bir süre kullanacağınızı bildiğiniz halde yeni bir türe bir sorgu için proje yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aec90-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="aec90-104">Projeksiyon içinde kullanmak için yeni bir tür oluşturmaya yönelik çok fazla iş vardır.</span><span class="sxs-lookup"><span data-stu-id="aec90-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="aec90-105">Bu örnekte daha verimli bir yaklaşım, bir anonim türe projem değildir.</span><span class="sxs-lookup"><span data-stu-id="aec90-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="aec90-106">Anonim türler sınıfı tanımlamanızı sağlar, sonra sınıfa bir ad vermeden bu sınıfın bir nesnesini bildirip başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="aec90-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="aec90-107">Anonim türler, bir *tanımlama*grubunun matematik kavramının C# uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="aec90-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="aec90-108">Matematiksel terim tanımlama grubu, tek, Çift, Üçlü, dörtlü, quintuple, n-Tuple dizisinden kaynakdır.</span><span class="sxs-lookup"><span data-stu-id="aec90-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="aec90-109">Belirli bir türün her biri, sınırlı bir nesne dizisine başvurur.</span><span class="sxs-lookup"><span data-stu-id="aec90-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="aec90-110">Bazen buna ad/değer çiftleri listesi denir.</span><span class="sxs-lookup"><span data-stu-id="aec90-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="aec90-111">Örneğin, [örnek XML dosyasındaki bir adresin içeriği: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) XML belgesi şu şekilde ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="aec90-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="aec90-112">Anonim bir türün bir örneğini oluşturduğunuzda, bunu bir sıra n grubu oluşturarak düşünmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="aec90-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="aec90-113">Yan tümcesinde bir tanımlama grubu oluşturan bir sorgu yazarsanız sorgu, `Select` `IEnumerable` kayıt düzeni döndürür.</span><span class="sxs-lookup"><span data-stu-id="aec90-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aec90-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="aec90-114">Example</span></span>  
 <span data-ttu-id="aec90-115">Bu örnekte `Select` yan tümce, anonim bir tür.</span><span class="sxs-lookup"><span data-stu-id="aec90-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="aec90-116">Örnek daha sonra `Dim` nesneyi oluşturmak için kullanır `IEnumerable` .</span><span class="sxs-lookup"><span data-stu-id="aec90-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="aec90-117">Döngü içinde `For Each` , yineleme değişkeni sorgu ifadesinde oluşturulan anonim türün bir örneği olur.</span><span class="sxs-lookup"><span data-stu-id="aec90-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="aec90-118">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="aec90-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="aec90-119">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="aec90-119">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="aec90-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aec90-120">See also</span></span>

- [<span data-ttu-id="aec90-121">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aec90-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
