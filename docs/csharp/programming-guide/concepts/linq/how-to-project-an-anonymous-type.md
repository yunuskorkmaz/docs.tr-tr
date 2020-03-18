---
title: Anonim bir tür (C#) nasıl yansıtılatır?
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 7797c8bfb12943af1ce7f975b170bf002aa7d6fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345728"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="72805-102">Anonim bir tür (C#) nasıl yansıtılatır?</span><span class="sxs-lookup"><span data-stu-id="72805-102">How to project an anonymous type (C#)</span></span>
<span data-ttu-id="72805-103">Bazı durumlarda, bu türü yalnızca kısa bir süre için kullanacağınızı biliyor olsanız bile, sorguyabilir.</span><span class="sxs-lookup"><span data-stu-id="72805-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="72805-104">Sadece projeksiyon kullanmak için yeni bir tür oluşturmak için ekstra iş bir sürü.</span><span class="sxs-lookup"><span data-stu-id="72805-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="72805-105">Bu durumda daha verimli bir yaklaşım anonim bir tür proje etmektir.</span><span class="sxs-lookup"><span data-stu-id="72805-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="72805-106">Anonim türler, sınıfa bir ad vermeden bir sınıf tanımlamanıza ve bu sınıfın bir nesnesini bildirmenize ve başlatmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72805-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="72805-107">Anonim türleri bir *tuple*matematiksel kavramının C # uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="72805-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="72805-108">Matematiksel terim tuple dizi tek, çift, üçlü, dörtlü, beşli, n-tuple kökenlidir.</span><span class="sxs-lookup"><span data-stu-id="72805-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="72805-109">Her biri belirli bir türde olan sonlu bir nesne dizisini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="72805-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="72805-110">Bazen bu ad/değer çiftleri listesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="72805-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="72805-111">Örneğin, Örnek XML Dosyasındaki bir adresin [içeriği: Tipik SatınAlma Siparişi (LINQ - XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML belgesi aşağıdaki gibi ifade edilebilir:</span><span class="sxs-lookup"><span data-stu-id="72805-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="72805-112">Anonim bir türbir örnek oluşturduğunuzda, bunu n sırasının bir tuple'ı oluşturmak olarak düşünmek uygundur.</span><span class="sxs-lookup"><span data-stu-id="72805-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="72805-113">`select` Yan tümcede bir tuple oluşturan bir sorgu yazarsanız, sorgu bir `IEnumerable` tuple döndürür.</span><span class="sxs-lookup"><span data-stu-id="72805-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72805-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="72805-114">Example</span></span>  
 <span data-ttu-id="72805-115">Bu örnekte, `select` yan tümce anonim bir türü projeleri.</span><span class="sxs-lookup"><span data-stu-id="72805-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="72805-116">Örnek daha `var` sonra nesneyi `IEnumerable` oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="72805-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="72805-117">`foreach` Döngü içinde, yineleme değişkeni sorgu ifadesinde oluşturulan anonim türbir örneği olur.</span><span class="sxs-lookup"><span data-stu-id="72805-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="72805-118">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Müşteriler ve Siparişler (LINQ-XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="72805-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="72805-119">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="72805-119">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  