---
title: XML Şemalarını Düzenleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
ms.openlocfilehash: b309c390ede3afc38122188337fa0dc3336e3ad5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292065"
---
# <a name="editing-xml-schemas"></a>XML Şemalarını Düzenleme

XML şeması düzenlenmesinin, şema nesne modeli 'nin (SOM) en önemli özelliklerinden biridir. SOM 'un şema öncesi derleme özelliklerinin tümü bir XML şemasında varolan değerleri değiştirmek için kullanılabilir. XML şeması daha sonra değişiklikleri yansıtacak şekilde yeniden derlenir.

SOM 'a yüklenen bir şemayı düzenlemenin ilk adımı şemanın gezedir. Bir şemayı düzenlemeye çalışmadan önce, SOM API 'sini kullanarak bir şemanın geçiş yapmaya alışmanız gerekir. Şema-derleme-bilgi kümesi 'nin (PSCı) ön ve son şema-derleme özelliklerini de tanımanız gerekir.

## <a name="editing-an-xml-schema"></a>XML şeması düzenleniyor

Bu bölümde, iki kod örneği sağlanır, ikisi de [derleme XML şemaları](building-xml-schemas.md) içinde oluşturulan müşteri şemasını düzenler konu. İlk kod örneği, öğesine yeni bir `PhoneNumber` öğesi ekler `Customer` ve ikinci kod örneği öğeye yeni bir `Title` öznitelik ekler `FirstName` . İlk örnek ayrıca, <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> İkinci kod örneği şema öncesi derleme koleksiyonunu kullandığında, şema sonrası-derleme koleksiyonunu müşteri şemasına geçme yöntemi olarak kullanır <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .

### <a name="phonenumber-element-example"></a>PhoneNumber öğesi örneği

Bu ilk kod örneği, `PhoneNumber` Müşteri şemasının öğesine yeni bir öğesi ekler `Customer` . Kod örneği aşağıdaki adımlarda müşteri şemasını düzenler.

1. Müşteri şemasını yeni bir <xref:System.Xml.Schema.XmlSchemaSet> nesneye ekler ve bunu derler. Şemayı okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları temsilci tarafından işlenir <xref:System.Xml.Schema.ValidationEventHandler> .

2. <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet> Özelliği üzerinde yineleerek derlenmiş nesneyi öğesinden alır <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> . Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.

3. , `PhoneNumber` <xref:System.Xml.Schema.XmlSchemaElement> `xs:string` Ve sınıflarını kullanarak basit tür kısıtlaması olan sınıfını kullanarak öğesi oluşturur <xref:System.Xml.Schema.XmlSchemaSimpleType> <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> , kısıtlamanın özelliğine bir model modeli ekler <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> ve kısıtlama, <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> basit türdeki ve basit tür özelliğine öğesi öğesine eklenir <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> `PhoneNumber` .

4. <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> Şema sonrası derleme koleksiyonu koleksiyonundaki her birinin üzerinde dolaşır <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .

5. Öğesi ise, sınıfını kullanarak <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"Customer"` `Customer` <xref:System.Xml.Schema.XmlSchemaComplexType> ve karmaşık türün dizi partiküyi kullanarak öğenin karmaşık türünü alır <xref:System.Xml.Schema.XmlSchemaSequence> .

6. Yeni öğeyi, `PhoneNumber` `FirstName` `LastName` sıranın ön şema derlemesini kullanarak var olan ve öğeleri içeren diziye ekler <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> .

7. Son olarak, değiştirilen <xref:System.Xml.Schema.XmlSchema> nesneyi sınıfının ve yöntemlerini kullanarak yeniden işler ve derler ve <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> konsola yazar.

Aşağıda kodun tamamı verilmiştir.

[!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
[!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
[!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]

Aşağıda, [XML şemaları oluşturma](building-xml-schemas.md) konusunda oluşturulan değiştirilmiş müşteri şeması yer almaktadır.

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
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />
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

Bu ikinci kod örneği, `Title` Müşteri şemasının öğesine yeni bir öznitelik ekler `FirstName` . İlk kod örneğinde, `FirstName` öğesinin türü `xs:string` . `FirstName`Öğesinin dize içeriğiyle birlikte bir özniteliğe sahip olması için, türü basit bir içerik uzantısı içerik modeli olan karmaşık bir türe değiştirilmelidir.

Kod örneği aşağıdaki adımlarda müşteri şemasını düzenler.

1. Müşteri şemasını yeni bir <xref:System.Xml.Schema.XmlSchemaSet> nesneye ekler ve bunu derler. Şemayı okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları temsilci tarafından işlenir <xref:System.Xml.Schema.ValidationEventHandler> .

2. <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet> Özelliği üzerinde yineleerek derlenmiş nesneyi öğesinden alır <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> . Şema derlendiğinden, Schema-Compilation-Infoset (PSCı) özelliklerine erişilebilir.

3. Sınıfını kullanarak öğesi için yeni bir karmaşık tür oluşturur `FirstName` <xref:System.Xml.Schema.XmlSchemaComplexType> .

4. `xs:string`Ve sınıflarını kullanarak temel türü ile yeni bir basit içerik uzantısı oluşturur <xref:System.Xml.Schema.XmlSchemaSimpleContent> <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> .

5. , `Title` <xref:System.Xml.Schema.XmlSchemaAttribute> ' A sahip sınıfını kullanarak yeni özniteliğini oluşturur <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> `xs:string` ve özniteliğini basit içerik uzantısına ekler.

6. Basit içeriğin içerik modelini basit içerik uzantısına ve karmaşık türün içerik modelini basit içeriğe ayarlar.

7. Yeni karmaşık türü, şema öncesi derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonuna ekler.

8. <xref:System.Xml.Schema.XmlSchemaObject>Şema öncesi derleme koleksiyonundaki her birinin üzerinde yinelenir <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> .

> [!NOTE]
> `FirstName`Öğe şemada genel bir öğe olmadığından, <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> veya <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonlarda kullanılamaz. Kod örneği, öğesini `FirstName` önce öğesini bularak konumlandırır `Customer` .
>
> İlk kod örneği, şema sonrası-derleme koleksiyonu kullanılarak şemanın yerine geçen <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> . Bu örnekte, <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> şemanın çapraz geçişini yapmak için şema öncesi derleme koleksiyonu kullanılır. Her iki koleksiyon de şemadaki genel öğelere erişim sağlarken, <xref:System.Xml.Schema.XmlSchema.Items%2A> şemadaki tüm genel öğeleri yinelemek ve herhangi BIR PSCI özelliği olmaması gerektiğinden, koleksiyonda yineleme daha fazla zaman alır. Psci koleksiyonları ( <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> , <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType> , vb <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType> .), genel öğelerine, özniteliklerine ve türlerine ve bunların pSCI özelliklerine doğrudan erişim sağlar.

1. <xref:System.Xml.Schema.XmlSchemaObject>Öğesi bir öğesi ise, sınıfını kullanarak <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"Customer"` `Customer` <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve karmaşık türün dizi partiküyi kullanarak öğenin karmaşık türünü alır <xref:System.Xml.Schema.XmlSchemaSequence> .

2. <xref:System.Xml.Schema.XmlSchemaParticle>Şema öncesi derleme koleksiyonundaki her birinin üzerinde yinelenir <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> .

3. Öğesi ise <xref:System.Xml.Schema.XmlSchemaParticle> , kim ise, <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> `"FirstName"` <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> `FirstName` öğesinin öğesini yeni `FirstName` karmaşık türe ayarlar.

4. Son olarak, değiştirilen <xref:System.Xml.Schema.XmlSchema> nesneyi sınıfının ve yöntemlerini kullanarak yeniden işler ve derler ve <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> konsola yazar.

Aşağıda kodun tamamı verilmiştir.

[!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
[!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
[!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]

Aşağıda, [XML şemaları oluşturma](building-xml-schemas.md) konusunda oluşturulan değiştirilmiş müşteri şeması yer almaktadır.

```xml
<?xml version="1.0" encoding=" utf-8"?>
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />
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
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](xml-schema-object-model-overview.md)
- [XML Şemaları Okuma ve Yazma](reading-and-writing-xml-schemas.md)
- [XML Şemaları Derleme](building-xml-schemas.md)
- [XML Şemalarını Çapraz Geçirme](traversing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](post-schema-compilation-infoset.md)
