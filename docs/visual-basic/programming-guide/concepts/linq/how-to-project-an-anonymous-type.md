---
title: 'Nasıl yapılır: Proje bir anonim türü (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: cc8e59ac1037fc173cb44d8c8ff344374c5766ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834575"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Nasıl yapılır: Proje bir anonim türü (Visual Basic)
Bazı durumlarda bu tür yalnızca kısa bir süre için kullanacağı bilseniz bile bir sorgu yeni bir tür için proje isteyebilirsiniz. Bu, birçok yalnızca projeksiyonda kullanmak için yeni bir tür oluşturmak için fazladan iş olur. Daha verimli bir yaklaşım için bu durumda, anonim bir tür için proje. Anonim türler bir sınıf tanımlama sonra bildirir ve sınıfı bir ad vererek olmadan söz konusu sınıfın bir nesnesi başlatılmaya olanak sağlar.  
  
 Anonim türler matematik kavramı, C# uygulaması bir *demet*. Matematik terimi demet tek dizisinden çift kaynaklanan üç, dört, beş kez, n-tanımlama grubu. Bu sınırlı dizisi ile nesneleri belirli bir türdeki her ifade eder. Bazen bu ad/değer çiftlerinin listesini denir. Örneğin, bir adres içeriğini [örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML belgesi ifade edilemez gibi:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Anonim bir türün örneğini oluşturduğunuzda, bunu order n tanımlama grubu oluşturma olarak düşünün kullanışlıdır. Bir grup içinde oluşturan bir sorgu yazma, `Select` sorgu yan tümcesi döndürür bir `IEnumerable` düzeninin.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `Select` yan tümcesi projeleri anonim bir tür. Ardından örnekte `Dim` oluşturmak için `IEnumerable` nesne. İçinde `For Each` döngüsünün yineleme değişkeni sorgu ifadesi içinde oluşturulan anonim türün bir örneğini haline gelir.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Projeksiyonlar ve Dönüşümler (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
