---
title: Anonim bir tür proje-LINQ to XML
description: Yansıtma içinde kullanmak için bir tür oluşturmak yerine anonim bir türde proje yapabilirsiniz. Bu makale, C# ve Visual Basic için bir örnek sağlar.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 5851492f075068337c60316664138dd09c97443b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553270"
---
# <a name="how-to-project-an-anonymous-type-linq-to-xml"></a>Anonim bir tür proje (LINQ to XML)

Bazı durumlarda, yeni bir türe bir sorgu proje yapmak isteyebilirsiniz, ancak sorgu yalnızca yeni tür için kullanılır. Türü oluşturmak yerine, bir anonim türde proje yapabilirsiniz. Anonim türler, önce bir türü açıkça tanımlamak zorunda kalmadan bir nesnedeki salt okunurdur özellikler kümesini kapsüllemek için kullanışlı bir yol sağlar. Yan tümcesinde anonim türde bir nesne oluşturan bir sorgu yazarsanız `select` , sorgu türden bir değer döndürür <xref:System.Collections.IEnumerable> .

Aşağıdaki örnek, iki özellik ile başlatılan anonim türdeki bir nesnenin oluşturulmasını gösterir `Amount` ve `Message` .

```csharp
var v = new { Amount = 108, Message = "Hello" };
```

```vb
Dim v = New With { .Amount = 108, .Message = "Hello" };
```

Her özelliğin türü derleyici tarafından algılanır. Tür adı derleyici tarafından oluşturulur ve kaynak kodu düzeyinde kullanılabilir değildir.

Anonim türler hakkında daha fazla bilgi için bkz.

- [Anonim Türler (C# Programlama Kılavuzu)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Anonim Türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

## <a name="example-project-an-anonymous-type-by-creating-objects-in-the-select-clause"></a>Örnek: yan tümcede nesneler oluşturarak anonim bir tür proje `select`

Bu örnekte `select` yan tümce, anonim bir tür. Örnek daha sonra `var` nesneyi oluşturmak için kullanır `IEnumerable` . Döngü içinde `foreach` , yineleme değişkeni sorgu ifadesinde oluşturulan anonim türün bir örneği olur.

Bu örnek, XML belgesi [örnek xml dosyasını kullanır: müşteriler ve siparişler](sample-xml-file-customers-orders.md).

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
GREAL:Great Lakes Food Market:Howard Snyder
HUNGC:Hungry Coyote Import Store:Yoshi Latimer
LAZYK:Lazy K Kountry Store:John Steel
LETSS:Let's Stop N Shop:Jaime Yorres
```

## <a name="see-also"></a>Ayrıca bkz.

- [Anonim Türler (C# Programlama Kılavuzu)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Anonim Türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
