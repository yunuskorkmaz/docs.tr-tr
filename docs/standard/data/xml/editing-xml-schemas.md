---
title: XML Şemalarını Düzenleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 119c4c13c90aeca8c14d2725d927c38be32212a6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308724"
---
# <a name="editing-xml-schemas"></a>XML Şemalarını Düzenleme
Bir XML şeması düzenleme şema nesne modeli (SOM) en önemli özelliklerinden biridir. Tüm SOM öncesi schema derleme özelliklerini bir XML Şeması mevcut değerleri değiştirmek için kullanılabilir. XML Şeması daha sonra bu değişiklikleri yansıtacak şekilde derlenebileceğini.  
  
 SOM yüklenen bir şema düzenleme ilk adımı, şema geçiş sağlamaktır. Bir şema düzenleme girişiminde bulunmadan önce SOM API'sini kullanarak bir şema geçiş ile ilgili bilgi sahibi olması gerekir. Öncesi ve sonrası schema derleme sonrası-schema-derleme-sonrası bilgi kümesi (PSCI) özellikleriyle ilgili bilgi sahibi olmalıdır.  
  
## <a name="editing-an-xml-schema"></a>Bir XML şema düzenleme  
 Bu bölümde, iki kod örneği sağlanmıştır, ikisi de oluşturulan müşteri şemasını düzenleme [XML şemaları derleme](../../../../docs/standard/data/xml/building-xml-schemas.md) konu. İlk örnek kod yeni bir ekler `PhoneNumber` öğesine `Customer` öğesi ve ikinci kod örneğinde yeni bir ekler `Title` özniteliğini `FirstName` öğesi. İlk örnek de sonrası-schema-derleme kullanır <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonun ikinci kod örneğinde sırasında müşteri şema geçiş aracı olarak kullandığı öncesi-schema-derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.  
  
### <a name="phonenumber-element-example"></a>PhoneNumber öğe örneği  
 Bu ilk kod örneğinde yeni bir ekler `PhoneNumber` öğesine `Customer` müşteri şema öğesi. Kod örneği, aşağıdaki adımlarda, müşteri şema düzenler.  
  
1. Yeni bir müşteri şema ekler <xref:System.Xml.Schema.XmlSchemaSet> nesnesi ve ardından derler. Herhangi bir şema doğrulama uyarıları ve okuma veya şema derleme hatalarla karşılaşıldı işlenir <xref:System.Xml.Schema.ValidationEventHandler> temsilci.  
  
2. Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesnesinden <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği. Şema derlendiğinden sonrası-Schema-derleme-sonrası bilgi kümesi (PSCI) özellikleri erişilebilir.  
  
3. Oluşturur `PhoneNumber` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaElement> sınıfı `xs:string` basit tür kısıtlama kullanarak <xref:System.Xml.Schema.XmlSchemaSimpleType> ve <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> sınıflar, bir desen modeli ekler <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> kısıtlama özelliğini ekler kısıtlamaya <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> basit tür ve basit türü için özellik <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> , `PhoneNumber` öğesi.  
  
4. Her yinelenir <xref:System.Xml.Schema.XmlSchemaElement> içinde <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> sonrası-schema-derleme koleksiyonu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu.  
  
5. Varsa <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> öğesidir `"Customer"`, karmaşık türü alır `Customer` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve kullanarak karmaşık tür dizisi parçacık <xref:System.Xml.Schema.XmlSchemaSequence> sınıfı.  
  
6. Yeni ekler `PhoneNumber` varolan içeren sıralı öğesine `FirstName` ve `LastName` öncesi-schema-derleme kullanarak öğeleri <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> dizisi koleksiyonu.  
  
7. Son olarak, yeniden işler ve değiştirilmiş derler <xref:System.Xml.Schema.XmlSchema> kullanarak nesne <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.  
  
 Tam kod örneği verilmiştir.  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 Oluşturulan değiştirilmiş müşteri Şeması aşağıdaki gibidir [XML şemaları derleme](../../../../docs/standard/data/xml/building-xml-schemas.md) konu.  
  
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
  
### <a name="title-attribute-example"></a>Başlık özniteliği örneği  
 Bu ikinci kod örneğinde yeni bir ekler `Title` özniteliğini `FirstName` müşteri şema öğesi. İlk kod örneğinde, türü `FirstName` öğesi `xs:string`. İçin `FirstName` dize içerik türü değiştirildi, karmaşık bir türü basit içerik uzantısı içerik modeli ile birlikte bir öznitelik için öğesi.  
  
 Kod örneği, aşağıdaki adımlarda, müşteri şema düzenler.  
  
1. Yeni bir müşteri şema ekler <xref:System.Xml.Schema.XmlSchemaSet> nesnesi ve ardından derler. Herhangi bir şema doğrulama uyarıları ve okuma veya şema derleme hatalarla karşılaşıldı işlenir <xref:System.Xml.Schema.ValidationEventHandler> temsilci.  
  
2. Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesnesinden <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği. Şema derlendiğinden sonrası-Schema-derleme-sonrası bilgi kümesi (PSCI) özellikleri erişilebilir.  
  
3. İçin yeni bir karmaşık türü oluşturur `FirstName` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı.  
  
4. Taban bir türü ile bir yeni basit içerik uzantısı oluşturur `xs:string`kullanarak <xref:System.Xml.Schema.XmlSchemaSimpleContent> ve <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> sınıfları.  
  
5. Yeni oluşturur `Title` kullanarak özniteliği <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfı ile bir <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> , `xs:string` ve öznitelik basit içerik uzantısı ekler.  
  
6. Basit içeriğin içerik modeli, basit içerik uzantı ve karmaşık türün basit içerik için içerik modeli için ayarlar.  
  
7. Yeni karmaşık tür öncesi-schema-derlemeye ekler <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.  
  
8. Her yinelenir <xref:System.Xml.Schema.XmlSchemaObject> derlemedeki öncesi-schema- <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.  
  
> [!NOTE]
>  Çünkü `FirstName` öğesi genel bir şema öğesi değil, mevcut değildir <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> veya <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonları. Kod örneği bulur `FirstName` ilk bulma tarafından öğesi `Customer` öğesi.  
>   
>  İlk örnek kod geçiş sonrası-schema-derleme kullanarak şemasını <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu. Bu örnekte, öncesi-schema-derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> toplama şema geçirmek için kullanılır. Her iki koleksiyon şema genel öğelere erişim sunarken, üzerinden yineleme <xref:System.Xml.Schema.XmlSchema.Items%2A> koleksiyonu olduğundan daha uzun süren şemadaki tüm genel öğeler üzerinde yinelenmelidir ve herhangi bir PSCI özelliği yok. PSCI koleksiyonları (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, vb.) kendi genel öğeler, öznitelikler ve türler ve PSCI özelliklerini doğrudan erişim sağlar.  
  
1. Varsa <xref:System.Xml.Schema.XmlSchemaObject> bir öğedir, <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> olduğu `"Customer"`, karmaşık türü alır `Customer` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve kullanarak karmaşık tür dizisi parçacık <xref:System.Xml.Schema.XmlSchemaSequence> sınıfı.  
  
2. Her yinelenir <xref:System.Xml.Schema.XmlSchemaParticle> derlemedeki öncesi-schema- <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> koleksiyonu.  
  
3. Varsa <xref:System.Xml.Schema.XmlSchemaParticle> bir öğedir kullanan kişinin <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> olduğu `"FirstName"`, ayarlar <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> , `FirstName` yeni öğe `FirstName` karmaşık tür.  
  
4. Son olarak, yeniden işler ve değiştirilmiş derler <xref:System.Xml.Schema.XmlSchema> kullanarak nesne <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.  
  
 Tam kod örneği verilmiştir.  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 Oluşturulan değiştirilmiş müşteri Şeması aşağıdaki gibidir [XML şemaları derleme](../../../../docs/standard/data/xml/building-xml-schemas.md) konu.  
  
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
