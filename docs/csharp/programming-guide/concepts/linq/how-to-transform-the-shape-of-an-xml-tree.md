---
title: 'Nasıl yapılır: XML ağacının (C#) şeklini dönüştürme'
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: c6f78decdcc32d202f4a0f1e51a012dce8aa7d6c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592227"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>Nasıl yapılır: XML ağacının (C#) şeklini dönüştürme
Bir XML belgesinin *şekli* öğe adlarına, öznitelik adlarına ve hiyerarşisinin özelliklerine başvurur.  
  
 Bazen bir XML belgesinin şeklini değiştirmeniz gerekir. Örneğin, var olan bir XML belgesini farklı öğe ve öznitelik adları gerektiren başka bir sisteme göndermeniz gerekebilir. Belgeyi, gereken şekilde silip yeniden adlandırarak, ancak işlevsel oluşturmayı kullanmak daha okunabilir ve sürdürülebilir kod ile sonuçlanır. İşlevsel oluşturma hakkında daha fazla bilgi için bkz. [Işlevsel oluşturma (LINQ to XML)C#()](./functional-construction-linq-to-xml.md).  
  
 İlk örnek, XML belgesi organizasyonunu değiştirir. Karmaşık öğeleri ağaçtaki bir konumdan diğerine taşımıştır.  
  
 Bu konudaki ikinci örnek, kaynak belgeden farklı bir şekle sahip bir XML belgesi oluşturur. Öğe adlarının büyük küçük harflerini değiştirir, bazı öğeleri yeniden adlandırır ve dışarı dönüştürülen ağacın bazı öğelerini kaynak ağacından bırakır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, ekli sorgu ifadeleri kullanarak bir XML dosyasının şeklini değiştirir.  
  
 Bu örnekteki kaynak XML belgesi, `Customers` `Root` tüm müşterileri içeren öğesi altında bir öğesi içerir. Ayrıca, `Orders` `Root` tüm siparişleri içeren öğesi altında bir öğesi de içerir. Bu örnek, her müşteriye ait siparişlerin `Orders` `Customer` öğesi içindeki bir öğede bulunduğu yeni bir XML ağacı oluşturur. Özgün belge ayrıca `Order` öğesi içindeki bir `CustomerID` öğesi de içerir; bu öğe, yeniden şekillendirilmiş belgeden kaldırılır.  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
 Bu örnek bazı öğeleri yeniden adlandırır ve bazı öznitelikleri öğelere dönüştürür.  
  
 Bir `ConvertAddress` nesne<xref:System.Xml.Linq.XElement> listesi döndüren kod çağırır. Yöntemin bağımsız değişkeni, `Address` `Type` özniteliğinin değeri olan karmaşık öğeyi belirleyen bir sorgudur. `"Shipping"`  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)).  
  
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
