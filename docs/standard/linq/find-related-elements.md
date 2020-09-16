---
title: İlgili öğeleri bulma-LINQ to XML
description: C# ve Visual Basic ' de LINQ to XML sorgu ve XPath kullanarak bir öğenin ve özniteliği aynı değere sahip olan bir öğenin değerini bulma hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: 385d454d19a12bfa0f90510d73a2961a93bbd5ee
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549607"
---
# <a name="how-to-find-related-elements-linq-to-xml"></a>İlgili öğeleri bulma (LINQ to XML)

Bu makalede, bir öğenin ve özniteliği aynı değere sahip bir öğenin değerini bulmak için C# ve Visual Basic içinde LINQ to XML sorgusunun ve XPath 'in nasıl kullanılacağı gösterilmektedir.

## <a name="example-find-the-value-of-one-element-and-an-element-whose-attribute-has-the-same-value"></a>Örnek: bir öğenin değerini ve özniteliği aynı değere sahip olan bir öğeyi bulun

Bu örnek, `Order` XML belgesi örnek XML dosyasındaki 12 aya öğesini bulur [: müşteriler ve siparişler](sample-xml-file-customers-orders.md)ve ardından bu sipariş için müşteriyi bulur. XPath ifadesi `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]` .

> [!NOTE]
> .NET sürümünde, bir listedeki dizin oluşturma işlemi sıfır tabanlıdır; diğer bir deyişle, 0 dizini ilk öğesine başvurur. XPath koşulunda bir düğümler koleksiyonuna dizin oluşturma tek tabanlıdır. Bu fark için bu örnek hesaplar.

```csharp
XDocument co = XDocument.Load("CustomersOrders.xml");

// LINQ to XML query
XElement customer1 =
    (from el in co.Descendants("Customer")
     where (string)el.Attribute("CustomerID") ==
          (string)(co
              .Element("Root")
              .Element("Orders")
              .Elements("Order")
              .ToList()[11]
              .Element("CustomerID"))
    select el)
    .First();

// An alternate way to write the query that avoids creation
// of a System.Collections.Generic.List:
XElement customer2 =
    (from el in co.Descendants("Customer")
     where (string)el.Attribute("CustomerID") ==
          (string)(co
              .Element("Root")
              .Element("Orders")
              .Elements("Order")
              .Skip(11).First()
              .Element("CustomerID"))
    select el)
    .First();

// XPath expression
XElement customer3 = co.XPathSelectElement(
  ".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]");

if (customer1 == customer2 && customer1 == customer3)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(customer1);
```

```vb
Dim co As XDocument = XDocument.Load("CustomersOrders.xml")

' LINQ to XML query
Dim customer1 As XElement = ( _
    From el In co...<Customer> _
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _
        ToList()(11).<CustomerID>(0).Value _
    Select el).First()

' An alternate way to write the query that avoids creation
' of a System.Collections.Generic.List:
Dim customer2 As XElement = ( _
    From el In co...<Customer> _
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _
        Skip(11).First().<CustomerID>(0).Value _
    Select el).First()

' XPath expression
Dim customer3 As XElement = co.XPathSelectElement _
    (".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]")

If customer1 Is customer2 And customer1 Is customer3 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(customer1)
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Results are identical
<Customer CustomerID="HUNGC">
  <CompanyName>Hungry Coyote Import Store</CompanyName>
  <ContactName>Yoshi Latimer</ContactName>
  <ContactTitle>Sales Representative</ContactTitle>
  <Phone>(503) 555-6874</Phone>
  <Fax>(503) 555-2376</Fax>
  <FullAddress>
    <Address>City Center Plaza 516 Main St.</Address>
    <City>Elgin</City>
    <Region>OR</Region>
    <PostalCode>97827</PostalCode>
    <Country>USA</Country>
  </FullAddress>
</Customer>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](./comparison-xpath-linq-xml.md)
