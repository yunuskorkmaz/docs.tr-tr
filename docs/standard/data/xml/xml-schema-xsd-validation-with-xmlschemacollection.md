---
description: 'Daha fazla bilgi edinin: XmlSchemaCollection ile XML şeması (XSD) doğrulaması'
title: XmlSchemaCollection ile XML Şeması (XSD) Doğrulaması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
ms.openlocfilehash: b0363f6d5f656591d56a1202f223ee9797abd26d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782695"
---
# <a name="xml-schema-xsd-validation-with-xmlschemacollection"></a>XmlSchemaCollection ile XML Şeması (XSD) Doğrulaması

XML <xref:System.Xml.Schema.XmlSchemaCollection> şeması tanım dili (xsd) şemalarında XML belgesini doğrulamak için kullanabilirsiniz. , <xref:System.Xml.Schema.XmlSchemaCollection> Şemaları, her doğrulama gerçekleştiğinde belleğe yüklenebilmeleri için, koleksiyonda depolayarak performansı geliştirir. Şema, şema koleksiyonunda varsa, `schemaLocation` koleksiyonda şemayı aramak için özniteliği kullanılır.  
  
> [!IMPORTANT]
> <xref:System.Xml.Schema.XmlSchemaCollection>Sınıf artık kullanımdan kalkmıştır ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfıyla değiştirilmiştir. Sınıf hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> bkz. [şema derlemesi için XmlSchemaSet](xmlschemaset-for-schema-compilation.md).  
  
 Aşağıdaki örnek, bir veri dosyasının kök öğesini gösterir.  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 Bu örnekte, özniteliğinin değeri, `targetNamespace` `urn:bookstore-schema` şemasına eklenirken kullanılan ad alanı olan <xref:System.Xml.Schema.XmlSchemaCollection> .  
  
 Aşağıdaki kod örneği öğesine bir XML şeması ekler <xref:System.Xml.Schema.XmlSchemaCollection> .  
  
```vb  
Dim xsc As New XmlSchemaCollection()  
' XML Schema.  
xsc.Add("urn:bookstore-schema", schema)
reader = New XmlTextReader(filename)  
vreader = New XmlValidatingReader(reader)  
vreader.Schemas.Add(xsc)  
```  
  
```csharp  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
// XML Schema.  
xsc.Add("urn:bookstore-schema", schema);  
reader = new XmlTextReader (filename);  
vreader = new XmlValidatingReader (reader);  
vreader.Schemas.Add(xsc);  
```  
  
 `targetNamespace`Özniteliği `namespaceURI` , özelliği için yöntemine eklediğinizde genellikle kullanılır <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> <xref:System.Xml.Schema.XmlSchemaCollection> . Şemasını öğesine eklemeden önce bir null başvurusu belirtebilirsiniz <xref:System.Xml.Schema.XmlSchemaCollection> . Boş bir dize ("") ad alanı olmayan şemalar için kullanılmalıdır. , <xref:System.Xml.Schema.XmlSchemaCollection> Ad alanı olmayan yalnızca bir şemaya sahip olabilir.  
  
 Aşağıdaki kod örneği, bir XML şeması olan HeadCount. xsd öğesini öğesine ekler <xref:System.Xml.Schema.XmlSchemaCollection> ve HeadCount.xml doğrular.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Schema  
  
Namespace ValidationSample  
  
   Class Sample  
  
      Public Shared Sub Main()  
         Dim tr As New XmlTextReader("HeadCount.xml")  
         Dim vr As New XmlValidatingReader(tr)  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd")  
         vr.ValidationType = ValidationType.Schema  
         AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler  
  
         While vr.Read()  
         End While  
         Console.WriteLine("Validation finished")  
      End Sub  
      ' Main  
  
      Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)  
         Console.WriteLine("***Validation error")  
         Console.WriteLine("Severity:{0}", args.Severity)  
         Console.WriteLine("Message:{0}", args.Message)  
      End Sub  
      ' ValidationHandler  
   End Class  
   ' Sample  
End Namespace  
' ValidationSample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Schema;  
  
namespace ValidationSample  
{  
   class Sample  
   {  
      public static void Main()  
      {  
         XmlTextReader tr = new XmlTextReader("HeadCount.xml");  
         XmlValidatingReader vr = new XmlValidatingReader(tr);  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd");  
         vr.ValidationType = ValidationType.Schema;  
         vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);  
  
         while(vr.Read());  
         Console.WriteLine("Validation finished");  
      }  
  
      public static void ValidationHandler(object sender, ValidationEventArgs args)  
      {  
         Console.WriteLine("***Validation error");  
         Console.WriteLine("\tSeverity:{0}", args.Severity);  
         Console.WriteLine("\tMessage  :{0}", args.Message);  
      }  
   }  
}  
```  
  
 Aşağıda, doğrulanacak HeadCount.xml giriş dosyasının içeriği özetlenmektedir.  
  
```xml  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 Aşağıda, tarafından doğrulanacak olan HeadCount. xsd XML şema dosyasının içeriği özetlenmektedir.  
  
```xml  
<xs:schema xmlns="xsdHeadCount" targetNamespace="xsdHeadCount" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name='HeadCount' type="HEADCOUNT"/>  
   <xs:complexType name="HEADCOUNT">  
      <xs:sequence>  
         <xs:element name='Name' type='xs:string' maxOccurs='unbounded'/>  
      </xs:sequence>  
      <xs:attribute name='division' type='xs:int' use='optional' default='8'/>  
   </xs:complexType>  
</xs:schema>  
```  
  
 Aşağıdaki kod örneği, alan oluşturur <xref:System.Xml.XmlValidatingReader> <xref:System.Xml.XmlTextReader> . sample4.xml giriş dosyası, sample4. xsd XML şemasına göre onaylanır.  
  
```vb  
Dim tr As New XmlTextReader("sample4.xml")  
Dim vr As New XmlValidatingReader(tr)  
vr.ValidationType = ValidationType.Schema  
vr.Schemas.Add("datatypesTest", "sample4.xsd")  
AddHandler vr.ValidationEventHandler, AddressOf ValidationCallBack  
While vr.Read()  
   Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name)  
End While  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("sample4.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
vr.ValidationType = ValidationType.Schema;  
        vr.Schemas.Add("datatypesTest", "sample4.xsd");  
vr.ValidationEventHandler += new ValidationEventHandler(ValidationCallBack);  
while(vr.Read()) {  
    Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name);  
    }  
```  
  
 Aşağıda, doğrulanacak sample4.xml giriş dosyasının içeriği özetlenmektedir.  
  
```xml  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 Aşağıda, sample4. xsd XML şema dosyasının içeriğine göre doğrulanacak olan içerikleri özetlenmektedir.  
  
```xml  
<xs:schema
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
    xmlns:tns="datatypesTest"
    targetNamespace="datatypesTest"  
    elementFormDefault="qualified">  
  
<xs:element name = "datatypes">  
  <xs:complexType>  
    <xs:all>  
        <xs:element name="number">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="number_1" type="xs:decimal" maxOccurs="unbounded"/>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
    </xs:all>  
  </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlParserContext>
- <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=nameWithType>
- <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=nameWithType>
- [XmlSchemaCollection Şema Derlemesi](xmlschemacollection-schema-compilation.md)
