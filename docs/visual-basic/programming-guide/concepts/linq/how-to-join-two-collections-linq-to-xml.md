---
title: 'Nasıl yapılır: Iki koleksiyonu birleştirin (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 404a43f52fce141b515da389090c81c57186f2e2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344528"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a>Nasıl yapılır: Iki koleksiyonu birleştirin (LINQ to XML) (Visual Basic)
XML belgesindeki bir öğe veya öznitelik, bazen başka bir öğe veya özniteliğe başvurabilir. Örneğin, [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML belgesi, müşterilerin ve siparişlerin listesinin bir listesini içerir. Her `Customer` öğesi bir `CustomerID` özniteliği içerir. Her `Order` öğesi bir `CustomerID` öğesi içerir. Her sırada `CustomerID` öğesi bir müşterinin `CustomerID` özniteliğine başvurur.  
  
 [Örnek xsd dosyası: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) , bu belgeyi doğrulamak için KULLANıLABILECEK bir xsd içerir. `Customer` öğesinin `CustomerID` özniteliğinin bir anahtar olduğunu ve her `CustomerID` öğesindeki `Order` öğesi ile her `CustomerID` öğesi arasında bir ilişki kurmayı oluşturmak için XSD 'nin `xs:key` ve `xs:keyref` özelliklerini kullanır.`Customer`  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], `Join` yan tümcesini kullanarak bu ilişkinin avantajlarından yararlanabilirsiniz.  
  
 Kullanılabilir dizin olmadığından, bu tür bir birleştirme çalışma zamanı performansına sahip olacaktır.  
  
 `Join`hakkında daha ayrıntılı bilgi için bkz. [JOIN işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `Customer` öğelerini `Order` öğelerine birleştirir ve siparişlerde `CompanyName` öğesini içeren yeni bir XML belgesi oluşturur.  
  
 Sorguyu yürütmeden önce örnek, belgenin örnek XSD dosyasındaki şemayla uyumlu olduğunu doğrular [: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md). Bu, JOIN yan tümcesinin her zaman çalışmasına de sağlar.  
  
 Bu sorgu ilk olarak tüm `Customer` öğelerini alır ve sonra bunları `Order` öğelerine birleştirir. Yalnızca, "K" dan büyük `CustomerID` olan müşterilere ait siparişleri seçer. Ardından, her bir sırada müşteri bilgilerini içeren yeni bir `Order` öğesini projeler.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
 Bu örnek şu XSD şemasını kullanır: [örnek xsd dosyası: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).  
  
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

- [Gelişmiş sorgu teknikleri (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
