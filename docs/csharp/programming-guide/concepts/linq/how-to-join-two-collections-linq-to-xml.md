---
title: İki koleksiyon nasıl katılır (LINQ to XML) (C#)
description: Bu C# örneği, LINQ to XML öğeleri diğer öğelere birleştirir ve yeni bir XML belgesi oluşturur.
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 10792ed4907e778b41821c9b32574bd8fc0ab35f
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104997"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>İki koleksiyon nasıl katılır (LINQ to XML) (C#)

XML belgesindeki bir öğe veya öznitelik, bazen başka bir öğe veya özniteliğe başvurabilir. Örneğin, [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML belgesi, müşterilerin ve siparişlerin listesinin bir listesini içerir. Her `Customer` öğe bir `CustomerID` özniteliği içerir. Her `Order` öğe bir `CustomerID` öğesi içerir. `CustomerID`Her siparişte bulunan öğe, `CustomerID` bir müşterinin özniteliği anlamına gelir.

[Örnek xsd dosyası: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md) , bu belgeyi doğrulamak için KULLANıLABILECEK bir xsd içerir. `xs:key`Özniteliğin ve özelliklerini kullanarak `xs:keyref` `CustomerID` `Customer` öğe özniteliğinin bir anahtar olduğunu ve her bir öğe `CustomerID` içindeki öğe ile her bir öğedeki özniteliği arasında bir ilişki kurmayı kullanır `Order` `CustomerID` `Customer` .

İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , yan tümcesini kullanarak bu ilişkiyi kullanabilirsiniz `join` .

Kullanılabilir dizin olmadığından, bu tür bir katılım düşük çalışma zamanı performansına sahip olacaktır.

Hakkında daha ayrıntılı bilgi için `join` bkz. [JOIN Operations (C#)](./join-operations.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek öğeleri öğelerine birleştirir `Customer` `Order` ve siparişlerdeki öğesini içeren yenı bir XML belgesi oluşturur `CompanyName` .

Sorguyu yürütmeden önce örnek, belgenin örnek XSD dosyasındaki şemayla uyumlu olduğunu doğrular [: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md). Bu, JOIN yan tümcesinin her zaman çalışmasına de sağlar.

Bu sorgu önce tüm `Customer` öğeleri alır ve ardından bunları `Order` öğelerine birleştirir. Yalnızca "K" dan büyük müşterilere ait siparişleri seçer `CustomerID` . Ardından `Order` , her bir sırada müşteri bilgilerini içeren yeni bir öğesi projeler.

Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).

Bu örnek şu XSD şemasını kullanır: [örnek xsd dosyası: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md).

Bu şekilde katılabilmek iyi bir işlem yapmaz. Birleşimler, doğrusal bir arama yoluyla yapılır. Performansla ilgili yardım için hiçbir karma tablo veya dizin yok.

```csharp
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", "CustomersOrders.xsd");

Console.Write("Attempting to validate, ");
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");

bool errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");

if (!errors)
{
    // Join customers and orders, and create a new XML document with
    // a different shape.

    // The new document contains orders only for customers with a
    // CustomerID > 'K'
    XElement custOrd = custOrdDoc.Element("Root");
    XElement newCustOrd = new XElement("Root",
        from c in custOrd.Element("Customers").Elements("Customer")
        join o in custOrd.Element("Orders").Elements("Order")
                   on (string)c.Attribute("CustomerID") equals
                      (string)o.Element("CustomerID")
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0
        select new XElement("Order",
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),
            new XElement("CompanyName", (string)c.Element("CompanyName")),
            new XElement("ContactName", (string)c.Element("ContactName")),
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))
        )
    );
    Console.WriteLine(newCustOrd);
}
```

Bu kod şu çıkışı oluşturur:

```output
Attempting to validate, custOrdDoc validated
<Root>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-03-21T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-05-22T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-06-25T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-10-27T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>6</EmployeeID>
    <OrderDate>1997-11-10T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>4</EmployeeID>
    <OrderDate>1998-02-12T00:00:00</OrderDate>
  </Order>
</Root>
```
