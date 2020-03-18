---
title: Bir XML ağacının şeklini dönüştürme (C#)
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 91f91ed6fea5371fae2ce67a413f4825f37af6c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347301"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>Bir XML ağacının şeklini dönüştürme (C#)
XML belgesinin *şekli,* öğe adlarını, öznitelik adlarını ve hiyerarşisinin özelliklerini ifade eder.  
  
 Bazen bir XML belgesinin şeklini değiştirmeniz gerekir. Örneğin, varolan bir XML belgesini farklı öğe ve öznitelik adları gerektiren başka bir sisteme göndermeniz gerekebilir. Öğeleri gerektiği gibi silip yeniden adlandırarak belgeyi gözden geçirebilirsiniz, ancak işlevsel yapı sonuçlarını daha okunabilir ve koruyabilir kodla kullanarak. Fonksiyonel yapı hakkında daha fazla bilgi için bkz: [Fonksiyonel Yapı (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).  
  
 İlk örnek, XML belgesinin kuruluşunu değiştirir. Karmaşık öğeleri ağaçtaki bir konumdan diğerine taşır.  
  
 Bu konudaki ikinci örnek, kaynak belgeden farklı bir şekle sahip bir XML belgesi oluşturur. Öğe adlarının gövdesini değiştirir, bazı öğeleri yeniden adlandırır ve kaynak ağaçtan bazı öğeleri dönüştürülmüş ağacın dışına bırakır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, katışılmış sorgu ifadelerini kullanarak bir XML dosyasının şeklini değiştirir.  
  
 Bu örnekteki kaynak XML `Customers` belgesi, `Root` tüm müşterileri içeren öğenin altında bir öğe içerir. Ayrıca tüm `Orders` siparişleri `Root` içeren öğe altında bir öğe içerir. Bu örnek, her müşteri için `Orders` `Customer` siparişlerin öğe içindeki bir öğede bulunduğu yeni bir XML ağacı oluşturur. Özgün belge de `CustomerID` `Order` öğebir öğe içerir; bu öğe yeniden şekillendirilen belgeden kaldırılır.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Müşteriler ve Siparişler (LINQ-XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
 Bu örnek, bazı öğeleri yeniden adlandırır ve bazı öznitelikleri öğelere dönüştürür.  
  
 Nesnelerin listesini döndüren kod çağrıları. `ConvertAddress` <xref:System.Xml.Linq.XElement> Yöntemin bağımsız değişkeni, özniteliğin `Address` değeri `"Shipping"`olan `Type` karmaşık öğeyi belirleyen bir sorgudur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Tipik SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
