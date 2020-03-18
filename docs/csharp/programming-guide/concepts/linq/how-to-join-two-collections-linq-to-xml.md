---
title: İki koleksiyona (LINQ - XML) (C#) nasıl katılanın?
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: a5044778bbfd9529faf5fe63c72076f6a973c815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345855"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>İki koleksiyona (LINQ - XML) (C#) nasıl katılanın?

XML belgesindeki bir öğe veya öznitelik bazen başka bir öğeye veya özniteliğe başvurabilir. Örneğin, [Örnek XML Dosyası: Müşteriler ve Siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML belgesi, bir müşteri listesi ve sipariş listesi içerir. Her `Customer` öğe `CustomerID` bir öznitelik içerir. Her `Order` öğe `CustomerID` bir öğe içerir. Her `CustomerID` siparişteki öğe, `CustomerID` müşterideki özniteliğe başvurur.

Konu [Örnek XSD Dosyası: Müşteriler ve Siparişler,](./sample-xsd-file-customers-and-orders1.md) bu belgeyi doğrulamak için kullanılabilecek bir XSD içerir. XSD'nin `xs:key` `xs:keyref` özelliklerini, `CustomerID` `Customer` öğenin özniteliğinin bir anahtar olduğunu belirlemek ve her `CustomerID` `Order` öğedeki `CustomerID` öğe ile öznitelik `Customer` arasında bir ilişki kurmak için kullanır.

Ile, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bu ilişkiden yan tümceyi `join` kullanarak yararlanabilirsiniz.

Kullanılabilir dizin olmadığından, bu tür birleştirmeler çalışma süresi performansı nın düşük olacaktır.

Hakkında `join`daha ayrıntılı bilgi için bkz: [Join Operations (C#)](./join-operations.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Customer` `Order` öğelere öğeleri birleştirir ve siparişlerde `CompanyName` öğeiçeren yeni bir XML belge oluşturur.

Sorguyu yürütmeden önce, örnek belgenin [Örnek XSD Dosyasındaki](./sample-xsd-file-customers-and-orders1.md)şema ile uyumlu olduğunu doğrular: Müşteriler ve Siparişler. Bu, birleştirme yan tümcesinin her zaman çalışmasını sağlar.

Bu sorgu önce `Customer` tüm öğeleri alır ve sonra `Order` öğelere katılır. Yalnızca "K"den `CustomerID` büyük müşteriler için siparişleri seçer. Daha sonra her `Order` sipariş içinde müşteri bilgilerini içeren yeni bir öğe yi yitir.

Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Müşteriler ve Siparişler (LINQ-XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).

Bu örnekte aşağıdaki XSD şeması kullanır: [Örnek XSD Dosyası: Müşteriler ve Siparişler.](./sample-xsd-file-customers-and-orders1.md)

Bu şekilde katılmak iyi bir performans sergilemeyecektir. Birleştirmeler doğrusal bir arama ile gerçekleştirilir. Performansa yardımcı olacak karma tablolar veya dizinler yoktur.

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
