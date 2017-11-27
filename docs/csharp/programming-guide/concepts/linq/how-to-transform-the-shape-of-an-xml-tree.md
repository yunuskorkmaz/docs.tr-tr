---
title: "Nasıl yapılır: bir XML ağacının (C#) şekil Dönüştür"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fd5b1351f8473aa2a1bd40992095a89fdfc38375
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>Nasıl yapılır: bir XML ağacının (C#) şekil Dönüştür
*Şekli* bir XML belgesi öğe adları, öznitelik adları ve özellikleri, hiyerarşinin başvuruyor.  
  
 Bazen, bir XML belgesi şeklini değiştirmek gerekir. Örneğin, var olan bir XML belgesi farklı öğe ve öznitelik adları gerektiren başka bir sisteme gönderme gerekebilir. Belgenin silmeyi ve daha okunabilir ve sürdürülebilir kodu gerekli, ancak kullanarak işlev yapım sonuç olarak öğeleri yeniden adlandırma gidebilir. İşlev oluşturma hakkında daha fazla bilgi için bkz: [işlevsel yapımı (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 İlk örnek XML belgesi organizasyonu değiştirir. Bu karmaşık öğeleri ağacında bir konumdan diğerine taşır.  
  
 Bu konudaki ikinci örnek kaynak belgedeki daha farklı bir şekli bir XML belgesi oluşturur. Öğe adları büyük küçük harf değiştirir, bazı öğelerin yeniden adlandırır ve bazı öğeler kaynak ağaç dönüştürülmüş ağaç dışında bırakır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod katıştırılmış sorgu ifadeleri kullanarak XML dosyasını şeklini değiştirir.  
  
 Bu örnekte kaynak XML belgesi içeriyor bir `Customers` öğesinin altında `Root` tüm müşteriler içeren öğe. Ayrıca içeren bir `Orders` öğesinin altında `Root` tüm siparişleri içeren öğe. Bu örnekte, her bir müşteri için siparişleri içerdiği yeni bir XML ağacı oluşturur bir `Orders` öğesi içinde `Customer` öğesi. Özgün belgeyi de içeren bir `CustomerID` öğesinde `Order` öğesi; yeniden şekilli belgeden kaldırılması bu öğe olacaktır.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
XElement newCustOrd =  
    new XElement("Root",  
        from cust in co.Element("Customers").Elements("Customer")  
        select new XElement("Customer",  
            cust.Attributes(),  
            cust.Elements(),  
            new XElement("Orders",  
                from ord in co.Element("Orders").Elements("Order")  
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")  
                select new XElement("Order",  
                    ord.Attributes(),  
                    ord.Element("EmployeeID"),  
                    ord.Element("OrderDate"),  
                    ord.Element("RequiredDate"),  
                    ord.Element("ShipInfo")  
                )  
            )  
        )  
    );  
Console.WriteLine(newCustOrd);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
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
    <Orders />  
  </Customer>  
  . . .  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bazı öğelerin yeniden adlandırır ve bazı öznitelikler öğelerine dönüştürür.  
  
 Kod çağrıları `ConvertAddress`, listesini döndürür <xref:System.Xml.Linq.XElement> nesneleri. Yöntemin bağımsız değişkeni belirleyen bir sorgudur `Address` karmaşık bir öğe burada `Type` özniteliği değerine sahip `"Shipping"`.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
static IEnumerable<XElement> ConvertAddress(XElement add)  
{  
    List<XElement> fragment = new List<XElement>() {  
        new XElement("NAME", (string)add.Element("Name")),  
        new XElement("STREET", (string)add.Element("Street")),  
        new XElement("CITY", (string)add.Element("City")),  
        new XElement("ST", (string)add.Element("State")),  
        new XElement("POSTALCODE", (string)add.Element("Zip")),  
        new XElement("COUNTRY", (string)add.Element("Country"))  
    };  
    return fragment;  
}  
  
static void Main(string[] args)  
{  
    XElement po = XElement.Load("PurchaseOrder.xml");  
    XElement newPo = new XElement("PO",  
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),  
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),  
        ConvertAddress(  
            (from el in po.Elements("Address")  
            where (string)el.Attribute("Type") == "Shipping"  
            select el)  
            .First()  
        )  
    );  
    Console.WriteLine(newPo);  
}  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projeksiyonlar ve dönüştürmeler (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
