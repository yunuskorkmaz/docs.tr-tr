---
title: İki koleksiyonu birleştirmek-LINQ to XML
description: Bir XSD dosyası, yeni öğe türleri oluşturmak için öğelerin katılmasını sağlamak üzere bir XML dosyasında ilişki kurabilir. Bu makale, C# ve öğeleri birleştiren ve yeni bir XML belgesi oluşturan Visual Basic bir örnek sağlar.
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2ab74f861cfd046e202a861378b8fd8792c7bac4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553381"
---
# <a name="how-to-join-two-collections-linq-to-xml"></a>İki koleksiyonu birleştirme (LINQ to XML)

Bir XSD dosyası, yeni öğe türleri oluşturmak için öğelerin katılmasını sağlamak üzere bir XML dosyasında ilişki kurabilir. Bu makale, C# ve öğeleri birleştiren ve yeni bir XML belgesi oluşturan Visual Basic bir örnek sağlar.

XML belgesindeki bir öğe veya öznitelik, bazen başka bir öğe veya özniteliğe başvurabilir. Örneğin, XML belgesi [örnek xml dosyası: müşteriler ve siparişler](sample-xml-file-customers-orders.md) , müşterilerin ve siparişlerin listesinin bir listesini içerir. Her `Customer` öğe bir `CustomerID` özniteliğe sahiptir ve her öğe `Order` bir öğesi içerir `CustomerID` . `CustomerID`Bir öğesindeki öğe değeri, `Order` `Customer` eşleşen bir öznitelik değerine sahip olan öğeye başvurur `CustomerID` .

[Örnek xsd dosyası: müşteriler ve siparişler](sample-xsd-file-customers-orders.md) , belgeyi doğrulamak için KULLANıLABILECEK bir xsd içerir `Customers and orders` . `xs:key`Özniteliğin ve özelliklerini kullanarak `xs:keyref` `CustomerID` `Customer` öğe özniteliğinin bir anahtar olduğunu ve öğelerin anahtar ve öğesi arasında bir ilişki oluşturmasını sağlar `CustomerID` `Order` .

LINQ to XML ile bu ilişkiden yararlanarak `join` müşteri bilgilerine sipariş bilgilerini katmak için yan tümcesini kullanabilirsiniz.

Hakkında daha ayrıntılı bilgi için `join` bkz. [JOIN Operations (C#)](../../csharp/programming-guide/concepts/linq/join-operations.md) ve [JOIN işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/join-operations.md).
> [!NOTE]
> Birleşimler, doğrusal aramalar kullanılarak yapılır. Arama performansını artırmak için hiç dizin yok.

## <a name="example-create-a-new-xml-document-that-has-customer-and-order-elements-joined"></a>Örnek: `Customer` ve öğelerine katılmış yeni BIR XML belgesi oluştur `Order`

Aşağıdaki örnek, örnek XML dosyası öğelerini birleştiren yeni bir XML belgesi oluşturur `Customer` [: müşteriler ve siparişler](sample-xml-file-customers-orders.md) `Order` öğeleri için ve `CompanyName` emirdeki öğesini içerir.

Sorguyu yürütmeden önce örnek, belgenin örnek XSD dosyasındaki şemayla uyumlu olduğunu doğrular [: müşteriler ve siparişler](sample-xsd-file-customers-orders.md). Bu, JOIN yan tümcesinin çalışır olmasını sağlar.

Sorgu yalnızca "K" dan büyük müşterilere yönelik siparişleri seçer `CustomerID` . BT projeleri `Order` her bir sırada müşteri bilgilerini içeren yeni öğeler.

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

```vb
Public Class Program
    Public Shared errors As Boolean = False

    Public Shared Function LamValidEvent(ByVal o As Object, _
                 ByVal e As ValidationEventArgs) As Boolean
        Console.WriteLine("{0}", e.Message)
        errors = True
    End Function

    Shared Sub Main()
        Dim schemas As New XmlSchemaSet()
        schemas.Add("", "CustomersOrders.xsd")

        Console.Write("Attempting to validate, ")
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")

        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))
        If errors Then
            Console.WriteLine("custOrdDoc did not validate")
        Else
            Console.WriteLine("custOrdDoc validated")
        End If

        If Not errors Then
            'Join customers and orders, and create a new XML document with
            ' a different shape.
            'The new document contains orders only for customers with a
            ' CustomerID > 'K'.
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault
            Dim newCustOrd As XElement = _
                <Root>
                    <%= From c In custOrd.<Customers>.<Customer> _
                        Join o In custOrd.<Orders>.<Order> _
                        On c.@CustomerID Equals o.<CustomerID>.Value _
                        Where c.@CustomerID.CompareTo("K") > 0 _
                        Select _
                        <Order>
                            <CustomerID><%= c.@CustomerID %></CustomerID>
                            <%= c.<CompanyName> %>
                            <%= c.<ContactName> %>
                            <%= o.<EmployeeID> %>
                            <%= o.<OrderDate> %>
                        </Order> _
                    %>
                </Root>
            Console.WriteLine(newCustOrd)
        End If
    End Sub
End Class
```

Bu örnek aşağıdaki çıktıyı üretir:

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
