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
# <a name="how-to-project-an-anonymous-type-c"></a>Nasıl yapılır: Proje anonim bir tür (C#)
Bazı durumlarda, yalnızca kısa bir süre bu tür kullanacağınız bilseniz bile bir sorgu yeni bir tür için proje isteyebilirsiniz. Yalnızca yansıtma kullanmak için yeni bir türü oluşturmak için ek iş çok karmaşıktır. Daha verimli bir yaklaşım için bu durumda olan anonim bir tür projeye. Anonim türler, bir sınıf tanımlama sonra bildirme ve bu sınıfın bir nesnesi sınıfı bir ad verip olmadan başlatma olanak tanır.  
  
 Anonim türler matematiksel kavramı, C# uygulaması olan bir *tanımlama grubu*. Matematik terim tanımlama grubu tek dizisinden çift kaynaklanan Üçlü, dört, beş kez, n-tanımlama grubu. Sınırlı dizisi nesneleri için belirli bir türdeki her başvuruyor. Bazen bu ad/değer çiftlerinin listesini denir. Örneğin, bir adres içeriğini [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML belgesi ifade edilir şekilde:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Anonim bir türün bir örneği oluşturduğunuzda, bunu sipariş n tanımlama grubu oluşturma olarak düşünün uygundur. İçinde bir tanımlama grubu oluşturur bir sorgu yazın, `select` yan tümcesi, sorgunun döndürdüğü bir `IEnumerable` kayıt.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `select` yan tümcesi projeleri anonim bir tür. Bu örnek daha sonra kullanır `var` oluşturmak için `IEnumerable` nesnesi. İçinde `foreach` döngü, yineleme değişkeni sorgu ifadesinde oluşturulan anonim türünün bir örneği haline gelir.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projeksiyonlar ve dönüştürmeler (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
