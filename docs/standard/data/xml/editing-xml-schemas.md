---
title: XML Şemalarını Düzenleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: d7d9f8e0d4ec2f343b50e68e942bf94e93576f25
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710953"
---
# <a name="editing-xml-schemas"></a>XML Şemalarını Düzenleme

XML şeması düzenlenmesinin, şema nesne modeli 'nin (SOM) en önemli özelliklerinden biridir. SOM 'un şema öncesi derleme özelliklerinin tümü bir XML şemasında varolan değerleri değiştirmek için kullanılabilir. XML şeması daha sonra değişiklikleri yansıtacak şekilde yeniden derlenir.

SOM 'a yüklenen bir şemayı düzenlemenin ilk adımı şemanın gezedir. Bir şemayı düzenlemeye çalışmadan önce, SOM API 'sini kullanarak bir şemanın geçiş yapmaya alışmanız gerekir. Şema-derleme-bilgi kümesi 'nin (PSCı) ön ve son şema-derleme özelliklerini de tanımanız gerekir.

## <a name="editing-an-xml-schema"></a>XML şeması düzenleniyor

Bu bölümde, iki kod örneği sağlanır, ikisi de [derleme XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) içinde oluşturulan müşteri şemasını düzenler konu. İlk `PhoneNumber` kod örneği, `Customer` öğesine yeni bir öğesi ekler ve ikinci kod örneği `Title` `FirstName` öğeye yeni bir öznitelik ekler. İlk örnek ayrıca, ikinci kod örneği şema öncesi derleme <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonunu kullandığında, şema sonrası-derleme koleksiyonunu müşteri şemasına geçme yöntemi olarak kullanır.

### <a name="phonenumber-element-example"></a>PhoneNumber öğesi örneği

Bu ilk kod örneği, müşteri şemasının `PhoneNumber` `Customer` öğesine yeni bir öğesi ekler. Kod örneği aşağıdaki adımlarda müşteri şemasını düzenler.

1. Müşteri şemasını yeni <xref:System.Xml.Schema.XmlSchemaSet> bir nesneye ekler ve bunu derler. Şemayı okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları <xref:System.Xml.Schema.ValidationEventHandler> temsilci tarafından işlenir.

2. Özelliği üzerinde <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet> yineleerek derlenmiş nesneyi öğesinden alır. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.

3. , `PhoneNumber` <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> `PhoneNumber` Ve sınıflarını kullanarak `xs:string` basit tür kısıtlaması olan sınıfını kullanarak öğesi oluşturur, kısıtlamanın özelliğine bir model modeli ekler ve kısıtlama, basit türdeki ve basit tür özelliğine öğesi öğesine <xref:System.Xml.Schema.XmlSchemaSimpleType> eklenir.

4. Şema sonrası derleme <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu koleksiyonundaki her birinin üzerinde dolaşır.

5. <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> Öğesi ise `"Customer"`, sınıfını kullanarak ve karmaşık türün `Customer` <xref:System.Xml.Schema.XmlSchemaComplexType> <xref:System.Xml.Schema.XmlSchemaSequence> dizi partiküyi kullanarak öğenin karmaşık türünü alır.

6. Yeni `PhoneNumber` öğeyi, sıranın ön şema derlemesini `FirstName` `LastName` <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kullanarak var olan ve öğeleri içeren diziye ekler.

7. Son olarak, <xref:System.Xml.Schema.XmlSchema> değiştirilen nesneyi <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> sınıfının ve yöntemlerini kullanarak yeniden işler ve derler ve konsola yazar.

Aşağıda kodun tamamı verilmiştir.

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

Aşağıda, [XML şemaları oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusunda oluşturulan değiştirilmiş müşteri şeması yer almaktadır.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="xs:string" />
        <xs:element name="LastName" type="tns:LastNameType" />
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>
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
```

### <a name="title-attribute-example"></a>Title özniteliği örneği

Bu ikinci kod örneği, müşteri şemasının `Title` `FirstName` öğesine yeni bir öznitelik ekler. İlk kod örneğinde, `FirstName` öğesinin türü. `xs:string` `FirstName` Öğesinin dize içeriğiyle birlikte bir özniteliğe sahip olması için, türü basit bir içerik uzantısı içerik modeli olan karmaşık bir türe değiştirilmelidir.

Kod örneği aşağıdaki adımlarda müşteri şemasını düzenler.

1. Müşteri şemasını yeni <xref:System.Xml.Schema.XmlSchemaSet> bir nesneye ekler ve bunu derler. Şemayı okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları <xref:System.Xml.Schema.ValidationEventHandler> temsilci tarafından işlenir.

2. Özelliği üzerinde <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet> yineleerek derlenmiş nesneyi öğesinden alır. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.

3. <xref:System.Xml.Schema.XmlSchemaComplexType> Sınıfını kullanarak `FirstName` öğesi için yeni bir karmaşık tür oluşturur.

4. Ve sınıflarını kullanarak temel türü `xs:string`ile yeni bir basit içerik uzantısı oluşturur. <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> <xref:System.Xml.Schema.XmlSchemaSimpleContent>

5. , ' A `Title` <xref:System.Xml.Schema.XmlSchemaAttribute> <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> sahip sınıfını kullanarak yeni özniteliğini oluşturur `xs:string` ve özniteliğini basit içerik uzantısına ekler.

6. Basit içeriğin içerik modelini basit içerik uzantısına ve karmaşık türün içerik modelini basit içeriğe ayarlar.

7. Yeni karmaşık türü, şema öncesi derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonuna ekler.

8. Şema öncesi derleme <xref:System.Xml.Schema.XmlSchemaObject> <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonundaki her birinin üzerinde yinelenir.

> [!NOTE]
> `FirstName` Öğe şemada genel bir öğe olmadığından, <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> veya <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonlarda kullanılamaz. Kod örneği, öğesini önce `FirstName` `Customer` öğesini bularak konumlandırır.
>
> İlk kod örneği, şema sonrası-derleme <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu kullanılarak şemanın yerine geçen. Bu örnekte, şemanın çapraz geçişini yapmak için şema öncesi <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> derleme koleksiyonu kullanılır. Her iki koleksiyon de şemadaki genel öğelere erişim sağlarken, şemadaki tüm genel öğeleri yinelemek ve <xref:System.Xml.Schema.XmlSchema.Items%2A> herhangi bir PSCI özelliği olmaması gerektiğinden, koleksiyonda yineleme daha fazla zaman alır. Psci koleksiyonları (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>vb.), genel öğelerine, özniteliklerine ve türlerine ve bunların pSCI özelliklerine doğrudan erişim sağlar.

1. <xref:System.Xml.Schema.XmlSchemaObject> Öğesi bir <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> öğesi ise, sınıfını kullanarak `"Customer"` `Customer` <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve karmaşık türün <xref:System.Xml.Schema.XmlSchemaSequence> dizi partiküyi kullanarak öğenin karmaşık türünü alır.

2. Şema öncesi derleme <xref:System.Xml.Schema.XmlSchemaParticle> <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> koleksiyonundaki her birinin üzerinde yinelenir.

3. <xref:System.Xml.Schema.XmlSchemaParticle> <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> Öğesi ise, kim `"FirstName"`ise, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> `FirstName` öğesinin öğesini yeni `FirstName` karmaşık türe ayarlar.

4. Son olarak, <xref:System.Xml.Schema.XmlSchema> değiştirilen nesneyi <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> sınıfının ve yöntemlerini kullanarak yeniden işler ve derler ve konsola yazar.

Aşağıda kodun tamamı verilmiştir.

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

Aşağıda, [XML şemaları oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusunda oluşturulan değiştirilmiş müşteri şeması yer almaktadır.

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
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
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
