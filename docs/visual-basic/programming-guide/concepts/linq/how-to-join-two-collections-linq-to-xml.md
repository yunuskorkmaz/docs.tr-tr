---
title: 'Nasıl yapılır: İki Koleksiyonu Birleştirme (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: dc3cfd19d990fa81e00f4781cb15bf07eb9a80ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398057"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a>Nasıl yapılır: Iki koleksiyonu birleştirin (LINQ to XML) (Visual Basic)
XML belgesindeki bir öğe veya öznitelik, bazen başka bir öğe veya özniteliğe başvurabilir. Örneğin, [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) XML belgesi, müşterilerin ve siparişlerin listesinin bir listesini içerir. Her `Customer` öğe bir `CustomerID` özniteliği içerir. Her `Order` öğe bir `CustomerID` öğesi içerir. `CustomerID`Her siparişte bulunan öğe, `CustomerID` bir müşterinin özniteliği anlamına gelir.  
  
 [Örnek xsd dosyası: müşteriler ve siparişler](sample-xsd-file-customers-and-orders.md) , bu belgeyi doğrulamak için KULLANıLABILECEK bir xsd içerir. `xs:key`Özniteliğin ve özelliklerini kullanarak `xs:keyref` `CustomerID` `Customer` öğe özniteliğinin bir anahtar olduğunu ve her bir öğe `CustomerID` içindeki öğe ile her bir öğedeki özniteliği arasında bir ilişki kurmayı kullanır `Order` `CustomerID` `Customer` .  
  
 İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , yan tümcesini kullanarak bu ilişkiyi kullanabilirsiniz `Join` .  
  
 Kullanılabilir dizin olmadığından, bu tür bir birleştirme çalışma zamanı performansına sahip olacaktır.  
  
 Hakkında daha ayrıntılı bilgi için `Join` bkz. [JOIN işlemleri (Visual Basic)](join-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek öğeleri öğelerine birleştirir `Customer` `Order` ve siparişlerdeki öğesini içeren yenı bir XML belgesi oluşturur `CompanyName` .  
  
 Sorguyu yürütmeden önce örnek, belgenin örnek XSD dosyasındaki şemayla uyumlu olduğunu doğrular [: müşteriler ve siparişler](sample-xsd-file-customers-and-orders.md). Bu, JOIN yan tümcesinin her zaman çalışmasına de sağlar.  
  
 Bu sorgu önce tüm `Customer` öğeleri alır ve ardından bunları `Order` öğelerine birleştirir. Yalnızca "K" dan büyük müşterilere ait siparişleri seçer `CustomerID` . Ardından `Order` , her bir sırada müşteri bilgilerini içeren yeni bir öğesi projeler.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
 Bu örnek şu XSD şemasını kullanır: [örnek xsd dosyası: müşteriler ve siparişler](sample-xsd-file-customers-and-orders.md).  
  
 Bu biçimde birleştirme işlemi çok iyi gerçekleştirmez. Birleşimler, doğrusal bir arama yoluyla yapılır. Performansla ilgili yardım için hiçbir karma tablo veya dizin yok.  
  
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
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş sorgu teknikleri (LINQ to XML) (Visual Basic)](advanced-query-techniques-linq-to-xml.md)
