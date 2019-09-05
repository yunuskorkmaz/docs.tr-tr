---
title: 'Nasıl yapılır: Iki koleksiyonu birleştirin (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 82083a24da9a5356a8ff8e8430b61bb5d41f7c72
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253570"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Nasıl yapılır: Iki koleksiyonu birleştirin (LINQ to XML) (C#)
XML belgesindeki bir öğe veya öznitelik, bazen başka bir öğe veya özniteliğe başvurabilir. Örneğin, [örnek xml dosyası: Müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML belgesi, müşterilerin ve siparişlerin listesinin bir listesini içerir. Her `Customer` öğe bir `CustomerID` özniteliği içerir. Her `Order` öğe bir `CustomerID` öğesi içerir. Her siparişte bulunan `CustomerID` `CustomerID` öğe, bir müşterinin özniteliği anlamına gelir.  
  
 [Örnek örnek xsd dosyası: Müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md) , bu belgeyi doğrulamak için kullanılabilecek bir xsd içerir. `xs:key` `CustomerID` `xs:keyref`Öğeözniteliğinin biranahtar`CustomerID` olduğunu ve her`Order` öğe ve içindeki öğe arasında bir ilişki oluşturmasını sağlamak için xsd 'nin ve özelliklerini kullanır. `Customer` `CustomerID` her`Customer` öğe için özniteliği.  
  
 İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], `join` yan tümcesini kullanarak bu ilişkiyi kullanabilirsiniz.  
  
 Kullanılabilir dizin olmadığından, bu tür bir birleştirme çalışma zamanı performansına sahip olacaktır.  
  
 Hakkında `join`daha ayrıntılı bilgi için bkz. [JOIN Operations (C#)](./join-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek öğeleri `Order` öğelerine birleştirir `Customer` ve siparişlerdeki `CompanyName` öğesini içeren yeni bir XML belgesi oluşturur.  
  
 Sorguyu yürütmeden önce örnek, belgenin [örnek xsd dosyasındaki şemayla uyumlu olduğunu doğrular: Müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md). Bu, JOIN yan tümcesinin her zaman çalışmasına de sağlar.  
  
 Bu sorgu önce tüm `Customer` öğeleri alır ve ardından bunları `Order` öğelerine birleştirir. Yalnızca "K" dan `CustomerID` büyük müşterilere ait siparişleri seçer. Ardından, her bir sırada `Order` müşteri bilgilerini içeren yeni bir öğesi projeler.  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 Bu örnek, aşağıdaki XSD şemasını kullanır: [Örnek XSD Dosyası: Müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md).  
  
 Bu biçimde birleştirme işlemi çok iyi gerçekleştirmez. Birleşimler, doğrusal bir arama yoluyla yapılır. Performansla ilgili yardım için hiçbir karma tablo veya dizin yok.  
  
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
