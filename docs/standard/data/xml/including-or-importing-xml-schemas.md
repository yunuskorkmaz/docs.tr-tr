---
title: XML Şemalarını Dahil Etme veya İçeri Aktarma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
ms.openlocfilehash: f6c2829d45db147c81592c00710f04168b40679e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287707"
---
# <a name="including-or-importing-xml-schemas"></a>XML Şemalarını Dahil Etme veya İçeri Aktarma
XML şeması `<xs:import />` ,, `<xs:include />` ve öğelerini içerebilir `<xs:redefine />` . Bu şema öğeleri, dahil edilen veya içeri aktaran şemanın yapısını tamamlamak için kullanılabilen diğer XML şemalarına başvurur. , <xref:System.Xml.Schema.XmlSchemaImport> <xref:System.Xml.Schema.XmlSchemaInclude> Ve <xref:System.Xml.Schema.XmlSchemaRedefine> sınıfları, şema nesne modeli (som) API 'sinde bu öğelerle eşlenir.  
  
## <a name="including-or-importing-an-xml-schema"></a>XML şeması ekleme veya Içeri aktarma  
 Aşağıdaki kod örneği, adres şeması ile [XML şemaları oluşturma](building-xml-schemas.md) konusunda oluşturulan müşteri şemasını tamamlar. Adres şeması ile müşterinin şeması, adres türlerini müşteri şemasında kullanılabilir hale getirir.  
  
 Adres şeması, `<xs:include />` `<xs:import />` olduğu gibi adres şemasının bileşenlerini kullanmak için ya da öğelerinden birini kullanarak ya da `<xs:redefine />` herhangi bir bileşeni, müşteri şemasının ihtiyaçlarına uyacak şekilde değiştirmek için bir öğe kullanılarak birleştirilebilir. Adres şeması, `targetNamespace` Müşteri şemasından farklı bir öğesine sahip olduğundan, `<xs:import />` öğesi ve bu nedenle içeri aktarma semantiği kullanılır.  
  
 Kod örneği aşağıdaki adımlarda adres şemasını içerir.  
  
1. Müşteri şemasını ve adres şemasını yeni bir <xref:System.Xml.Schema.XmlSchemaSet> nesneye ekler ve bunları derler. Şemaları okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları temsilci tarafından işlenir <xref:System.Xml.Schema.ValidationEventHandler> .  
  
2. <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet> Özelliği üzerinde yineleme yaparak, ' den hem müşteri hem de adres şemaları için derlenmiş nesneleri alır <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> . Şemaların derlenmesi nedeniyle, şema sonrası derleme-bilgi kümesi (PSCı) özelliklerine erişilebilir.  
  
3. Bir <xref:System.Xml.Schema.XmlSchemaImport> nesnesi oluşturur, <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> içeri aktarmanın özelliğini adres şemasının ad alanına ayarlar, <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> içeri aktarmanın özelliğini <xref:System.Xml.Schema.XmlSchema> Adres şemasının nesnesine ayarlar ve içeri aktarma özelliğini <xref:System.Xml.Schema.XmlSchema.Includes%2A> Müşteri şemasının özelliğine ekler.  
  
4. <xref:System.Xml.Schema.XmlSchema>Sınıfının ve yöntemlerini kullanarak müşteri şemasının değiştirilen nesnesini yeniden işler ve derler <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> ve konsola yazar.  
  
5. Son olarak, müşteri şemasına içeri aktarılan tüm şemaları, müşterinin şeması özelliğini kullanarak konsola özyinelemeli olarak yazar <xref:System.Xml.Schema.XmlSchema.Includes%2A> . <xref:System.Xml.Schema.XmlSchema.Includes%2A>Özelliği, bir şemaya eklenen tüm içerme, içeri aktarmalar veya tekrar tanımlama işlemleri için erişim sağlar.  
  
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
  
 ,, Ve öğeleri ve sınıfları hakkında daha fazla bilgi için `<xs:import />` `<xs:include />` `<xs:redefine />` <xref:System.Xml.Schema.XmlSchemaImport> <xref:System.Xml.Schema.XmlSchemaInclude> <xref:System.Xml.Schema.XmlSchemaRedefine> bkz. [W3C XML şeması](https://www.w3.org/XML/Schema) ve <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı sınıfı başvuru belgeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](xml-schema-object-model-overview.md)
- [XML Şemaları Okuma ve Yazma](reading-and-writing-xml-schemas.md)
- [XML Şemaları Derleme](building-xml-schemas.md)
- [XML Şemalarını Çapraz Geçirme](traversing-xml-schemas.md)
- [XML Şemalarını Düzenleme](editing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](xmlschemaset-for-schema-compilation.md)
