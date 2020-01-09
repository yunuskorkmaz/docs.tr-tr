---
title: İki koleksiyon nasıl katılır (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: a5044778bbfd9529faf5fe63c72076f6a973c815
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345855"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>İki koleksiyon nasıl katılır (LINQ to XML) (C#)

XML belgesindeki bir öğe veya öznitelik, bazen başka bir öğe veya özniteliğe başvurabilir. Örneğin, [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML belgesi, müşterilerin ve siparişlerin listesinin bir listesini içerir. Her `Customer` öğesi bir `CustomerID` özniteliği içerir. Her `Order` öğesi bir `CustomerID` öğesi içerir. Her sırada `CustomerID` öğesi bir müşterinin `CustomerID` özniteliğine başvurur.

[Örnek xsd dosyası: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md) , bu belgeyi doğrulamak için KULLANıLABILECEK bir xsd içerir. `Customer` öğesinin `CustomerID` özniteliğinin bir anahtar olduğunu ve her `CustomerID` öğesindeki `Order` öğesi ile her `CustomerID` öğesi arasında bir ilişki kurmayı oluşturmak için XSD 'nin `xs:key` ve `xs:keyref` özelliklerini kullanır.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], `join` yan tümcesini kullanarak bu ilişkinin avantajlarından yararlanabilirsiniz.

Kullanılabilir dizin olmadığından, bu tür bir katılım düşük çalışma zamanı performansına sahip olacaktır.

`join`hakkında daha ayrıntılı bilgi için bkz. [JOIN Operations (C#)](./join-operations.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek `Customer` öğelerini `Order` öğelerine birleştirir ve siparişlerde `CompanyName` öğesini içeren yeni bir XML belgesi oluşturur.

Sorguyu yürütmeden önce örnek, belgenin örnek XSD dosyasındaki şemayla uyumlu olduğunu doğrular [: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md). Bu, JOIN yan tümcesinin her zaman çalışmasına de sağlar.

Bu sorgu ilk olarak tüm `Customer` öğelerini alır ve sonra bunları `Order` öğelerine birleştirir. Yalnızca, "K" dan büyük `CustomerID` olan müşterilere ait siparişleri seçer. Ardından, her bir sırada müşteri bilgilerini içeren yeni bir `Order` öğesini projeler.

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

Bu kod aşağıdaki çıktıyı üretir:

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
