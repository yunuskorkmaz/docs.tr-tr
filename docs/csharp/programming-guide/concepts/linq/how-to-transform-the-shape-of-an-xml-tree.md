---
title: 'Nasıl yapılır: Bir XML ağacının şeklini dönüştürme (C#)'
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 535f528d347e0c72ddaaab74ea78b47993a873a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701716"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>Nasıl yapılır: Bir XML ağacının şeklini dönüştürme (C#)
*Şekli* alt öğe adları, öznitelik adları ve özellikleri, hiyerarşinin bir XML'sini belge başvuruyor.  
  
 Bazen, bir XML belgesi şeklini değiştirmek gerekir. Örneğin, var olan bir XML belgesi farklı öğe ve öznitelik adları gerektiren başka bir sisteme gönderme gerekebilir. Belgede, silme ve gerekli, ancak kullanarak işlevsel oluşturma sonuçları daha okunabilir ve sürdürülebilir kod öğeleri yeniden adlandırma gidilemedi. İşlevsel oluşturma hakkında daha fazla bilgi için bkz: [işlevsel oluşturma (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 İlk örnek, XML belgesi kuruluş değiştirir. Bu karmaşık öğe ağacında bir konumdan diğerine taşır.  
  
 Bu konudaki ikinci örnek, kaynak belgedeki daha farklı bir şekilde bir XML belgesi oluşturur. Öğe adları büyük küçük harfleri değiştirir, bazı öğelerin yeniden adlandırır ve bazı öğeleri kaynak ağaç dönüştürülmüş ağaç dışında bırakır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, katıştırılmış sorgu ifadeleri kullanarak bir XML dosyası şeklini değiştirir.  
  
 Bu örnekte kaynak XML belgesinde içeren bir `Customers` öğesi altında `Root` tüm müşteriler içeren öğe. Ayrıca içerdiği bir `Orders` öğesi altında `Root` tüm siparişleri içeren öğe. Bu örnekte, her bir müşterinin siparişlerini içerdiği yeni bir XML ağacı oluşturur bir `Orders` öğesiyle `Customer` öğesi. Özgün belgeyi de içeren bir `CustomerID` öğesinde `Order` öğesi; yeniden şekillendirilmiş belgeden kaldırılması bu öğe olacaktır.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
 Bu örnek, bazı öğelerin yeniden adlandırır ve bazı öznitelikler öğesine dönüştürür.  
  
 Kod çağrıları `ConvertAddress`, listesini döndürür <xref:System.Xml.Linq.XElement> nesneleri. Yöntem bağımsız değişkeninin belirleyen bir sorgudur `Address` karmaşık bir öğe olduğu `Type` öznitelik değerine sahip `"Shipping"`.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Projeksiyonlar ve Dönüşümler (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
