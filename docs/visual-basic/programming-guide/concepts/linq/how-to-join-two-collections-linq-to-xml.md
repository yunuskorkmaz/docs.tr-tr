---
title: "Nasıl yapılır: iki koleksiyonları (LINQ-XML) birleştirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c4850013184b35dcb0b30455a62cead30394103c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a>Nasıl yapılır: iki koleksiyonları (LINQ-XML) birleştirme (Visual Basic)
Bazen bir öğe veya öznitelik bir XML belgesi başka bir öğe veya öznitelik başvurabilir. Örneğin, [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML belgesi, müşterilerin listesini ve siparişleri listesini içerir. Her `Customer` öğesi içeren bir `CustomerID` özniteliği. Her `Order` öğesi içeren bir `CustomerID` öğesi. `CustomerID` Her sipariş öğesinde başvurduğu `CustomerID` bir müşteri özniteliği.  
  
 Konu [örnek XSD dosyası: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) bu belgeyi doğrulamak için kullanılan bir XSD içerir. Kullandığı `xs:key` ve `xs:keyref` , kurmak için XSD özelliklerini `CustomerID` özniteliği `Customer` öğesidir bir anahtarı ve arasında bir ilişki oluşturmak için `CustomerID` her öğesinde `Order` öğesi ve `CustomerID` her özniteliği `Customer` öğesi.  
  
 İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu ilişkinin kullanarak yararlanabilirsiniz `Join` yan tümcesi.  
  
 Kullanılabilir herhangi bir dizin olduğundan zayıf çalışma zamanı performans böyle birleştirme'nin elde edersiniz unutmayın.  
  
 Hakkında ayrıntılı bilgi için `Join`, bkz: [birleştirme işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek birleştirmeler `Customer` öğelerine `Order` öğeleri ve içeren yeni bir XML belgesi oluşturur `CompanyName` siparişleri öğesinde.  
  
 Sorguyu çalıştırmadan önce örnek belge şeması ile uyumlu doğrular [örnek XSD dosyası: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md). Bu birleştirme yan tümcesi her zaman çalışmasını sağlar.  
  
 Bu sorgu önce tüm alır `Customer` öğeleri ve bunları birleştirir `Order` öğeleri. Yalnızca siparişleri sahip müşteriler için seçtiği bir `CustomerID` "K" büyüktür. Ardından yeni bir proje `Order` her sipariş içinde müşteri bilgilerini içeren öğe.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
 Bu örnekte aşağıdaki XSD şema kullanır: [örnek XSD dosyası: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).  
  
 Bu şekilde birleştirme çok iyi gerçekleştirmediğini unutmayın. Birleştirmeler doğrusal arama gerçekleştirilir. Karma tabloları veya performansla yardımcı olması için dizin yok.  
  
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
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş sorgu teknikler (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
