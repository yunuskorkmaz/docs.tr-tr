---
title: Anonim bir tür proje yapma (C#)
description: C# ' de anonim bir türe sorgu projesini nasıl oluşturacağınızı öğrenin. Anonim bir türün kullanılması, yalnızca kısa bir süre kullanmak için yeni bir tür oluşturmaktan daha kolay olabilir.
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 6598796a4ba95362340f2551b1da6ac6d857eaae
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104629"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="790a1-104">Anonim bir tür proje yapma (C#)</span><span class="sxs-lookup"><span data-stu-id="790a1-104">How to project an anonymous type (C#)</span></span>
<span data-ttu-id="790a1-105">Bazı durumlarda, bu türü yalnızca kısa bir süre kullanacağınızı bildiğiniz halde yeni bir türe bir sorgu için proje yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="790a1-105">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="790a1-106">Projeksiyon içinde kullanmak için yeni bir tür oluşturmaya yönelik çok fazla iş vardır.</span><span class="sxs-lookup"><span data-stu-id="790a1-106">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="790a1-107">Bu örnekte daha verimli bir yaklaşım, bir anonim türe projem değildir.</span><span class="sxs-lookup"><span data-stu-id="790a1-107">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="790a1-108">Anonim türler sınıfı tanımlamanızı sağlar, sonra sınıfa bir ad vermeden bu sınıfın bir nesnesini bildirip başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="790a1-108">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="790a1-109">Anonim türler, bir *tanımlama*grubunun matematik kavramının C# uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="790a1-109">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="790a1-110">Matematiksel terim tanımlama grubu, tek, Çift, Üçlü, dörtlü, quintuple, n-Tuple dizisinden kaynakdır.</span><span class="sxs-lookup"><span data-stu-id="790a1-110">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="790a1-111">Belirli bir türün her biri, sınırlı bir nesne dizisine başvurur.</span><span class="sxs-lookup"><span data-stu-id="790a1-111">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="790a1-112">Bazen buna ad/değer çiftleri listesi denir.</span><span class="sxs-lookup"><span data-stu-id="790a1-112">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="790a1-113">Örneğin, [örnek XML dosyasındaki bir adresin içeriği: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML belgesi şu şekilde ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="790a1-113">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="790a1-114">Anonim bir türün bir örneğini oluşturduğunuzda, bunu bir sıra n grubu oluşturarak düşünmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="790a1-114">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="790a1-115">Yan tümcesinde bir tanımlama grubu oluşturan bir sorgu yazarsanız sorgu, `select` `IEnumerable` kayıt düzeni döndürür.</span><span class="sxs-lookup"><span data-stu-id="790a1-115">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="790a1-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="790a1-116">Example</span></span>  
 <span data-ttu-id="790a1-117">Bu örnekte `select` yan tümce, anonim bir tür.</span><span class="sxs-lookup"><span data-stu-id="790a1-117">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="790a1-118">Örnek daha sonra `var` nesneyi oluşturmak için kullanır `IEnumerable` .</span><span class="sxs-lookup"><span data-stu-id="790a1-118">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="790a1-119">Döngü içinde `foreach` , yineleme değişkeni sorgu ifadesinde oluşturulan anonim türün bir örneği olur.</span><span class="sxs-lookup"><span data-stu-id="790a1-119">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="790a1-120">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="790a1-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="790a1-121">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="790a1-121">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  