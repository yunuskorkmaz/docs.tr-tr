---
title: XSD kullanarak doğrulama (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 29830457b63f36dd401a412364060339344f35cb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347247"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a>XSD kullanarak doğrulama (LINQ to XML) (C#)
<xref:System.Xml.Schema> ad alanı, bir xml ağacının bir XML şeması tanım dili (XSD) dosyasına göre doğrulanmasını kolaylaştıran uzantı yöntemleri içerir. Daha fazla bilgi için <xref:System.Xml.Schema.Extensions.Validate%2A> yöntemi belgelerine bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir <xref:System.Xml.Schema.XmlSchemaSet>oluşturur ve sonra iki <xref:System.Xml.Linq.XDocument> nesnesini şema kümesine göre doğrular. Belgelerden biri geçerli, diğeri değildir.  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, XML belgesinin [örnek XML dosyasından bulunduğunu doğrular: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) [örnek xsd dosyasından şema başına geçerlidir: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md). Sonra kaynak XML belgesini değiştirir. İlk müşterinin `CustomerID` özniteliğini değiştirir. Değişiklik sonrasında, siparişler var olmayan bir müşteriye başvuracaktır, bu nedenle XML belgesi artık doğrulanmaz.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 Bu örnek şu XSD şemasını kullanır: [örnek xsd dosyası: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md).  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [XML ağaçları oluşturma (C#)](creating-xml-trees-linq-to-xml-2.md)
