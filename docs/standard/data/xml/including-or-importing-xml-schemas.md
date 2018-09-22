---
title: Dahil veya XML şemaları içeri aktarma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b26ebfa327d849f75b1ac5295b66600aeb377e1e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580180"
---
# <a name="including-or-importing-xml-schemas"></a>Dahil veya XML şemaları içeri aktarma
Bir XML Şeması içerebilir `<xs:import />`, `<xs:include />`, ve `<xs:redefine />` öğeleri. Bu şema öğeleri içerir veya bunları alır şemasının yapısı desteklemek için kullanılabilecek diğer XML şemaları bakın. <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> Ve <xref:System.Xml.Schema.XmlSchemaRedefine> sınıflarını, eşlemek için bu öğeleri içinde şema nesne modeli (SOM) API.  
  
## <a name="including-or-importing-an-xml-schema"></a>Dahil veya bir XML Şeması içeri aktarma  
 Aşağıdaki kod örneği oluşturulan müşteri şema tamamlayan [XML şemaları derleme](../../../../docs/standard/data/xml/building-xml-schemas.md) adresi şemasıyla konu. Adresi şemasını müşteri şemasıyla ek adres türleri müşteri şema kullanılabilir hale getirir.  
  
 Adresi şemasını kullanarak birleştirilebilir `<xs:include />` veya `<xs:import />` bileşenlerini adresi şeması olarak kullanılacak öğelerin- ya da kullanarak bir `<xs:redefine />` bileşenlerinin müşteri şema gerek uyacak şekilde değiştirmek için öğesi. Adresi şemasını sahip olduğu bir `targetNamespace` müşteri şema farklı `<xs:import />` öğesi ve bu nedenle alma semantiği kullanılır.  
  
 Kod örneği, aşağıdaki adımlarda adresi şemasını içerir.  
  
1.  Müşteri şeması ve adresi şeması yeni bir ekler <xref:System.Xml.Schema.XmlSchemaSet> nesne ve bunları derler. Herhangi bir şema doğrulama uyarıları ve okuma veya şemaları derlenirken karşılaşılan hataları tarafından işlenen <xref:System.Xml.Schema.ValidationEventHandler> temsilci.  
  
2.  Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesneler için müşteri ve adresi şemalardan <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği. Şemaları derlendiğinden sonrası-Schema-derleme-sonrası bilgi kümesi (PSCI) özellikleri erişilebilir.  
  
3.  Oluşturur bir <xref:System.Xml.Schema.XmlSchemaImport> nesne, kümeleri <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> adresi Şema ad alanı için içeri aktarma özelliğini ayarlar <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> Al özelliğini <xref:System.Xml.Schema.XmlSchema> nesnesi adresi şemasının ve alma işlemi ekler <xref:System.Xml.Schema.XmlSchema.Includes%2A> Müşteri şeması özelliği.  
  
4.  Yeniden işler ve değiştirilmiş derler <xref:System.Xml.Schema.XmlSchema> şeması kullanarak müşteri nesnesi <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.  
  
5.  Son olarak, yinelemeli olarak tüm konsol kullanarak müşteri Şemayı içeri aktarılan şema Yazar <xref:System.Xml.Schema.XmlSchema.Includes%2A> müşteri şema özelliği. <xref:System.Xml.Schema.XmlSchema.Includes%2A> Özelliği tüm erişim sağlar, içeri aktarmalar veya yeniden tanımlama bir şemaya eklenen içerir.  
  
 Tam kod örneği ve konsoluna yazılan müşteri ve adresi şemaları aşağıda verilmiştir.  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 Hakkında daha fazla bilgi için `<xs:import />`, `<xs:include />`, ve `<xs:redefine />` öğeleri ve <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> ve <xref:System.Xml.Schema.XmlSchemaRedefine> sınıfları için bkz [W3C XML Şeması](https://www.w3.org/XML/Schema) ve <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı sınıf başvuru belgeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
- [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
- [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)  
- [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
