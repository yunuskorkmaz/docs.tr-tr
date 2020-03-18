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
# <a name="how-to-project-an-anonymous-type-c"></a>Anonim bir tür (C#) nasıl yansıtılatır?
Bazı durumlarda, bu türü yalnızca kısa bir süre için kullanacağınızı biliyor olsanız bile, sorguyabilir. Sadece projeksiyon kullanmak için yeni bir tür oluşturmak için ekstra iş bir sürü. Bu durumda daha verimli bir yaklaşım anonim bir tür proje etmektir. Anonim türler, sınıfa bir ad vermeden bir sınıf tanımlamanıza ve bu sınıfın bir nesnesini bildirmenize ve başlatmanıza olanak sağlar.  
  
 Anonim türleri bir *tuple*matematiksel kavramının C # uygulamasıdır. Matematiksel terim tuple dizi tek, çift, üçlü, dörtlü, beşli, n-tuple kökenlidir. Her biri belirli bir türde olan sonlu bir nesne dizisini ifade eder. Bazen bu ad/değer çiftleri listesi olarak adlandırılır. Örneğin, Örnek XML Dosyasındaki bir adresin [içeriği: Tipik SatınAlma Siparişi (LINQ - XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML belgesi aşağıdaki gibi ifade edilebilir:  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Anonim bir türbir örnek oluşturduğunuzda, bunu n sırasının bir tuple'ı oluşturmak olarak düşünmek uygundur. `select` Yan tümcede bir tuple oluşturan bir sorgu yazarsanız, sorgu bir `IEnumerable` tuple döndürür.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `select` yan tümce anonim bir türü projeleri. Örnek daha `var` sonra nesneyi `IEnumerable` oluşturmak için kullanır. `foreach` Döngü içinde, yineleme değişkeni sorgu ifadesinde oluşturulan anonim türbir örneği olur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Müşteriler ve Siparişler (LINQ-XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  