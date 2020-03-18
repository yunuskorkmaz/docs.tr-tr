---
title: XSD (LINQ - XML) (C#) kullanımı nasıl doğrulanır?
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 29830457b63f36dd401a412364060339344f35cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347247"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a>XSD (LINQ - XML) (C#) kullanımı nasıl doğrulanır?
Ad <xref:System.Xml.Schema> alanı, xml şema tanım dili (XSD) dosyasına karşı bir XML ağacını doğrulamayı kolaylaştıran uzantı yöntemleri içerir. Daha fazla bilgi <xref:System.Xml.Schema.Extensions.Validate%2A> için yöntem belgelerine bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, şema <xref:System.Xml.Schema.XmlSchemaSet>kümesine <xref:System.Xml.Linq.XDocument> karşı iki nesneyi doğrular. Belgelerden biri geçerli, diğeri geçerli değil.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Örnek XML Dosyasından XML belgesinin geçerli olduğunu [doğrular: Müşteriler ve Siparişler (LINQ-XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) Örnek [XSD Dosyasından](./sample-xsd-file-customers-and-orders1.md)şema başına geçerlidir: Müşteriler ve Siparişler. Daha sonra kaynak XML belgedeğiştirir. İlk müşterideki `CustomerID` özniteliği değiştirir. Değişiklikten sonra, siparişler var olmayan bir müşteriye başvurur, böylece XML belgesi artık doğrulanmaz.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Müşteriler ve Siparişler (LINQ-XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 Bu örnekte aşağıdaki XSD şeması kullanır: [Örnek XSD Dosyası: Müşteriler ve Siparişler.](./sample-xsd-file-customers-and-orders1.md)  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [XML Ağaçları Oluşturma (C#)](creating-xml-trees-linq-to-xml-2.md)
