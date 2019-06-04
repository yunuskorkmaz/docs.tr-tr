---
title: 'Nasıl yapılır: Anonim tip yansıtma (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 68b008d70474c927a7911dc77e60afb634035b77
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485132"
---
# <a name="how-to-project-an-anonymous-type-c"></a>Nasıl yapılır: Anonim tip yansıtma (C#)
Bazı durumlarda bu tür yalnızca kısa bir süre için kullanacağı bilseniz bile bir sorgu yeni bir tür için proje isteyebilirsiniz. Bu, birçok yalnızca projeksiyonda kullanmak için yeni bir tür oluşturmak için fazladan iş olur. Daha verimli bir yaklaşım için bu durumda, anonim bir tür için proje. Anonim türler bir sınıf tanımlama sonra bildirir ve sınıfı bir ad vererek olmadan söz konusu sınıfın bir nesnesi başlatılmaya olanak sağlar.  
  
 Anonim türler matematik kavramı, C# uygulaması bir *demet*. Matematik terimi demet tek dizisinden çift kaynaklanan üç, dört, beş kez, n-tanımlama grubu. Bu sınırlı dizisi ile nesneleri belirli bir türdeki her ifade eder. Bazen bu ad/değer çiftlerinin listesini denir. Örneğin, bir adres içeriğini [örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML belgesi ifade edilemez gibi:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Anonim bir türün örneğini oluşturduğunuzda, bunu order n tanımlama grubu oluşturma olarak düşünün kullanışlıdır. Bir grup içinde oluşturan bir sorgu yazma, `select` sorgu yan tümcesi döndürür bir `IEnumerable` düzeninin.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `select` yan tümcesi projeleri anonim bir tür. Ardından örnekte `var` oluşturmak için `IEnumerable` nesne. İçinde `foreach` döngüsünün yineleme değişkeni sorgu ifadesi içinde oluşturulan anonim türün bir örneğini haline gelir.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  