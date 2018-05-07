---
title: 'Nasıl yapılır: Proje anonim bir türü (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 13500bc606cb99a4264e04657f4a0a8090f07174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Nasıl yapılır: Proje anonim bir türü (Visual Basic)
Bazı durumlarda, yalnızca kısa bir süre bu tür kullanacağınız bilseniz bile bir sorgu yeni bir tür için proje isteyebilirsiniz. Yalnızca yansıtma kullanmak için yeni bir türü oluşturmak için ek iş çok karmaşıktır. Daha verimli bir yaklaşım için bu durumda olan anonim bir tür projeye. Anonim türler, bir sınıf tanımlama sonra bildirme ve bu sınıfın bir nesnesi sınıfı bir ad verip olmadan başlatma olanak tanır.  
  
 Anonim türler matematiksel kavramı, C# uygulaması olan bir *tanımlama grubu*. Matematik terim tanımlama grubu tek dizisinden çift kaynaklanan Üçlü, dört, beş kez, n-tanımlama grubu. Sınırlı dizisi nesneleri için belirli bir türdeki her başvuruyor. Bazen bu ad/değer çiftlerinin listesini denir. Örneğin, bir adres içeriğini [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML belgesi ifade edilir şekilde:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Anonim bir türün bir örneği oluşturduğunuzda, bunu sipariş n tanımlama grubu oluşturma olarak düşünün uygundur. İçinde bir tanımlama grubu oluşturur bir sorgu yazın, `Select` yan tümcesi, sorgunun döndürdüğü bir `IEnumerable` kayıt.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `Select` yan tümcesi projeleri anonim bir tür. Bu örnek daha sonra kullanır `Dim` oluşturmak için `IEnumerable` nesnesi. İçinde `For Each` döngü, yineleme değişkeni sorgu ifadesinde oluşturulan anonim türünün bir örneği haline gelir.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projeksiyonlar ve dönüştürmeler (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
