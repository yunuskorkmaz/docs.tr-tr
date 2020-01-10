---
title: XML Şemalarını Dahil Etme veya İçeri Aktarma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
ms.openlocfilehash: d9a18876d8a5ba3067aa35c617b1e20fce0411f5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710784"
---
# <a name="including-or-importing-xml-schemas"></a>XML Şemalarını Dahil Etme veya İçeri Aktarma
Bir XML şeması `<xs:import />`, `<xs:include />`ve `<xs:redefine />` öğeleri içerebilir. Bu şema öğeleri, dahil edilen veya içeri aktaran şemanın yapısını tamamlamak için kullanılabilen diğer XML şemalarına başvurur. <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> ve <xref:System.Xml.Schema.XmlSchemaRedefine> sınıfları, şema nesne modeli (SOM) API 'sinde bu öğelere eşlenir.  
  
## <a name="including-or-importing-an-xml-schema"></a>XML şeması ekleme veya Içeri aktarma  
 Aşağıdaki kod örneği, adres şeması ile [XML şemaları oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusunda oluşturulan müşteri şemasını tamamlar. Adres şeması ile müşterinin şeması, adres türlerini müşteri şemasında kullanılabilir hale getirir.  
  
 Adres şeması, olduğu gibi adres şemasının bileşenlerini kullanmak için `<xs:include />` veya `<xs:import />` öğeleri kullanılarak eklenebilir veya bir `<xs:redefine />` öğesi kullanarak bileşenlerini müşteri şemasının gereksinimlerine uyacak şekilde değiştirebilirsiniz. Adres şeması, müşteri şemasından farklı bir `targetNamespace` sahip olduğundan, `<xs:import />` öğesi ve bu nedenle içeri aktarma semantiği kullanılır.  
  
 Kod örneği aşağıdaki adımlarda adres şemasını içerir.  
  
1. Müşteri şemasını ve adres şemasını yeni bir <xref:System.Xml.Schema.XmlSchemaSet> nesnesine ekler ve sonra bunları derler. Şemaları okuma veya derleme ile karşılaşılan tüm şema doğrulama uyarıları ve hataları <xref:System.Xml.Schema.ValidationEventHandler> temsilcisi tarafından işlenir.  
  
2. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğini çağırarak <xref:System.Xml.Schema.XmlSchemaSet> hem müşteri hem de adres şemaları için derlenen <xref:System.Xml.Schema.XmlSchema> nesnelerini alır. Şemaların derlenmesi nedeniyle, şema sonrası derleme-bilgi kümesi (PSCı) özelliklerine erişilebilir.  
  
3. <xref:System.Xml.Schema.XmlSchemaImport> nesnesi oluşturur, almanın <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> özelliğini adres şemasının ad alanına ayarlar, içeri aktarmanın <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> özelliğini adres şemasının <xref:System.Xml.Schema.XmlSchema> nesnesine ayarlar ve içeri aktarma özelliğini müşteri şemasının <xref:System.Xml.Schema.XmlSchema.Includes%2A> özelliğine ekler.  
  
4. <xref:System.Xml.Schema.XmlSchemaSet> sınıfının <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerini kullanarak müşteri şemasının değiştirilen <xref:System.Xml.Schema.XmlSchema> nesnesini yeniden işler ve derler ve konsola yazar.  
  
5. Son olarak, müşteri şemasına içeri aktarılan tüm şemaları, müşteri şemasının <xref:System.Xml.Schema.XmlSchema.Includes%2A> özelliğini kullanarak konsola özyinelemeli olarak yazar. <xref:System.Xml.Schema.XmlSchema.Includes%2A> özelliği, bir şemaya eklenen tüm içerme, içeri aktarmalar veya tekrar tanımlama işlemleri için erişim sağlar.  
  
 Aşağıda, tüm kod örneği ve konsoluna yazılan müşteri ve adres şemaları verilmiştir.  
  
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
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
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
  
 `<xs:import />`, `<xs:include />`ve `<xs:redefine />` öğeleri ve <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> ve <xref:System.Xml.Schema.XmlSchemaRedefine> sınıfları hakkında daha fazla bilgi için bkz. [W3C XML şeması](https://www.w3.org/XML/Schema) ve <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı sınıfı başvuru belgeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
