---
title: XML 'den metin dosyaları oluşturma-LINQ to XML
description: C# ve Visual Basic bir XML dosyasından virgülle ayrılmış değerler (CSV) metin dosyası oluşturmak için kullanabilirsiniz. Bu makale bir örnek sağlar.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 9ad283f7-7cac-42ff-bf32-92aa866e6883
ms.openlocfilehash: 2650d223d542b3582fa8cd2a00f4b880ef04e5dc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552980"
---
# <a name="how-to-generate-text-files-from-xml-linq-to-xml"></a>XML 'den metin dosyaları oluşturma (LINQ to XML)

Bu makalede, bir XML dosyasından bir virgülle ayrılmış değerler (CSV) metin dosyası oluşturmak için C# ve Visual Basic kullanmayı gösteren bir örnek sunulmaktadır.

## <a name="example-generate-a-csv-file-from-an-xml-document"></a>Örnek: bir XML belgesinden CSV dosyası oluşturma

Bu örnek, XML belgesinden örnek XML dosyasından bir CSV dosyası oluşturur [: müşteriler ve siparişler](sample-xml-file-customers-orders.md).

C# sürümü, `Aggregate` tek bir ifadede dosyayı oluşturmak için yöntem sözdizimini ve işlecini kullanır. Daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi (C#)](../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

Visual Basic sürümü, dizeler koleksiyonunu tek bir dizeye toplamak için yordamsal kodu kullanır.

```csharp
XElement custOrd = XElement.Load("CustomersOrders.xml");
string csv =
    (from el in custOrd.Element("Customers").Elements("Customer")
    select
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}",
            (string)el.Attribute("CustomerID"),
            (string)el.Element("CompanyName"),
            (string)el.Element("ContactName"),
            (string)el.Element("ContactTitle"),
            (string)el.Element("Phone"),
            (string)el.Element("FullAddress").Element("Address"),
            (string)el.Element("FullAddress").Element("City"),
            (string)el.Element("FullAddress").Element("Region"),
            (string)el.Element("FullAddress").Element("PostalCode"),
            (string)el.Element("FullAddress").Element("Country"),
            Environment.NewLine
        )
    )
    .Aggregate(
        new StringBuilder(),
        (sb, s) => sb.Append(s),
        sb => sb.ToString()
    );
Console.WriteLine(csv);
```

```vb
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")
Dim strCollection As IEnumerable(Of String) = _
    From el In custOrd.<Customers>.<Customer> _
    Select _
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}", _
            el.@CustomerID, _
            el.<CompanyName>.Value, _
            el.<ContactName>.Value, _
            el.<ContactTitle>.Value, _
            el.<Phone>.Value, _
            el.<FullAddress>.<Address>.Value, _
            el.<FullAddress>.<City>.Value, _
            el.<FullAddress>.<Region>.Value, _
            el.<FullAddress>.<PostalCode>.Value, _
            el.<FullAddress>.<Country>.Value, _
            Environment.NewLine _
        )
Dim sb As StringBuilder = New StringBuilder()
For Each str As String In strCollection
    sb.Append(str)
Next
Console.WriteLine(sb.ToString())
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)](../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
