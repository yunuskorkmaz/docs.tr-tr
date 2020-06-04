---
title: 'Nasıl yapılır: Anonim Tip Yansıtma'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 459602eb7ede0bd055e00d3c7620cb95ec5408ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396486"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Nasıl yapılır: anonim bir tür proje (Visual Basic)
Bazı durumlarda, bu türü yalnızca kısa bir süre kullanacağınızı bildiğiniz halde yeni bir türe bir sorgu için proje yapmak isteyebilirsiniz. Projeksiyon içinde kullanmak için yeni bir tür oluşturmaya yönelik çok fazla iş vardır. Bu örnekte daha verimli bir yaklaşım, bir anonim türe projem değildir. Anonim türler sınıfı tanımlamanızı sağlar, sonra sınıfa bir ad vermeden bu sınıfın bir nesnesini bildirip başlatabilir.  
  
 Anonim türler, bir *tanımlama*grubunun matematik kavramının C# uygulamasıdır. Matematiksel terim tanımlama grubu, tek, Çift, Üçlü, dörtlü, quintuple, n-Tuple dizisinden kaynakdır. Belirli bir türün her biri, sınırlı bir nesne dizisine başvurur. Bazen buna ad/değer çiftleri listesi denir. Örneğin, [örnek XML dosyasındaki bir adresin içeriği: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) XML belgesi şu şekilde ifade edilebilir:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Anonim bir türün bir örneğini oluşturduğunuzda, bunu bir sıra n grubu oluşturarak düşünmek kullanışlıdır. Yan tümcesinde bir tanımlama grubu oluşturan bir sorgu yazarsanız sorgu, `Select` `IEnumerable` kayıt düzeni döndürür.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Select` yan tümce, anonim bir tür. Örnek daha sonra `Dim` nesneyi oluşturmak için kullanır `IEnumerable` . Döngü içinde `For Each` , yineleme değişkeni sorgu ifadesinde oluşturulan anonim türün bir örneği olur.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
