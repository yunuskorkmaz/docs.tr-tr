---
title: Dahil olmak üzere veya XML şemalarını içeri aktarma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2f83128f47a687e75a7db9bb36c487fa1f5bb6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573074"
---
# <a name="including-or-importing-xml-schemas"></a>Dahil olmak üzere veya XML şemalarını içeri aktarma
Bir XML Şeması içerebilir `<xs:import />`, `<xs:include />`, ve `<xs:redefine />` öğeleri. Bu şema öğeleri içerir veya bunları alır şema yapısını desteklemek için kullanılan diğer XML şemaları bakın. <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> Ve <xref:System.Xml.Schema.XmlSchemaRedefine> map sınıfları, bu öğelere içinde şema nesne modeli (SOM) API.  
  
## <a name="including-or-importing-an-xml-schema"></a>Dahil olmak üzere veya bir XML Şeması içeri aktarma  
 Aşağıdaki kod örneğinde oluşturulan müşteri şeması tamamlayan [yapı XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) adresi şema konu. Müşteri şeması adresi şemasını ile ekleme adres türleri müşteri şemasında kullanılabilir hale getirir.  
  
 Adresi şemasını kullanılarak birleştirilebilir `<xs:include />` veya `<xs:import />` adresi şema bileşenlerinin kullanmak için öğeleri- ya da kullanarak bir `<xs:redefine />` öğesi bileşenlerini müşteri şeması gerek uyacak şekilde değiştirin. Adresi şemasını sahip olduğu bir `targetNamespace` müşteri şeması, farklı `<xs:import />` öğesi ve bu nedenle içeri aktarma özelliklerini kullanılır.  
  
 Kod örneği, aşağıdaki adımlarda adresi şemasını içerir.  
  
1.  Müşteri şeması ve adres şeması yeni bir ekler <xref:System.Xml.Schema.XmlSchemaSet> nesne ve bunları derler. Şema doğrulama uyarıları ve okuma veya şemaları derleme karşılaşılan hataları tarafından işlenen <xref:System.Xml.Schema.ValidationEventHandler> temsilci.  
  
2.  Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesneler için müşteri ve adres şemaları <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği. Sonrası-Schema-derleme-bilgi (PSCI) özellikleri şemaları derlenmiş olduğundan, erişilebilir.  
  
3.  Oluşturur bir <xref:System.Xml.Schema.XmlSchemaImport> nesnesi, ayarlar <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> adresi Şema ad alanını alma işlemi özelliğini ayarlar <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> alma işlemi özelliğinin <xref:System.Xml.Schema.XmlSchema> adresi şemasını nesnesinin ve alma işlemi ekler <xref:System.Xml.Schema.XmlSchema.Includes%2A> Müşteri şeması özelliği.  
  
4.  Yeniden işler ve değiştirilen derler <xref:System.Xml.Schema.XmlSchema> kullanarak müşteri şema nesnesi <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.  
  
5.  Son olarak, yinelemeli olarak tüm konsolunu kullanarak müşteri şeması içeri aktarılan şemaların Yazar <xref:System.Xml.Schema.XmlSchema.Includes%2A> müşteri şeması özelliği. <xref:System.Xml.Schema.XmlSchema.Includes%2A> Özelliği, tüm erişim sağlar, içeri aktarmalar ya da yeniden tanımlama bir şemaya eklenen içerir.  
  
 Tam kod örneği ve konsola yazılan müşteri ve adres şemaları verilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
