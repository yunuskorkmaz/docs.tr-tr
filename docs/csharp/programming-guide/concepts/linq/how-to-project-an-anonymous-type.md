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
# <a name="how-to-project-an-anonymous-type-c"></a>Anonim bir tür proje yapma (C#)
Bazı durumlarda, bu türü yalnızca kısa bir süre kullanacağınızı bildiğiniz halde yeni bir türe bir sorgu için proje yapmak isteyebilirsiniz. Projeksiyon içinde kullanmak için yeni bir tür oluşturmaya yönelik çok fazla iş vardır. Bu örnekte daha verimli bir yaklaşım, bir anonim türe projem değildir. Anonim türler sınıfı tanımlamanızı sağlar, sonra sınıfa bir ad vermeden bu sınıfın bir nesnesini bildirip başlatabilir.  
  
 Anonim türler, bir *tanımlama*grubunun matematik kavramının C# uygulamasıdır. Matematiksel terim tanımlama grubu, tek, Çift, Üçlü, dörtlü, quintuple, n-Tuple dizisinden kaynakdır. Belirli bir türün her biri, sınırlı bir nesne dizisine başvurur. Bazen buna ad/değer çiftleri listesi denir. Örneğin, [örnek XML dosyasındaki bir adresin içeriği: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML belgesi şu şekilde ifade edilebilir:  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Anonim bir türün bir örneğini oluşturduğunuzda, bunu bir sıra n grubu oluşturarak düşünmek kullanışlıdır. Yan tümcesinde bir tanımlama grubu oluşturan bir sorgu yazarsanız sorgu, `select` `IEnumerable` kayıt düzeni döndürür.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `select` yan tümce, anonim bir tür. Örnek daha sonra `var` nesneyi oluşturmak için kullanır `IEnumerable` . Döngü içinde `foreach` , yineleme değişkeni sorgu ifadesinde oluşturulan anonim türün bir örneği olur.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
 Bu kod şu çıkışı oluşturur:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  