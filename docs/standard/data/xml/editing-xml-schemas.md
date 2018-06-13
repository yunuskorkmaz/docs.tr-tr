---
title: XML şemaları düzenleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38519ee90578d0bc13689216fb5674653ead4c19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577221"
---
# <a name="editing-xml-schemas"></a>XML şemaları düzenleme
Bir XML şeması düzenleme şema nesne modeli (SOM) en önemli özelliklerinden biridir. Tüm SOM öncesi schema derleme özelliklerinin bir XML şeması var olan değerleri değiştirmek için kullanılabilir. XML şema değişiklikleri yansıtacak şekilde sonra derlenebileceğini.  
  
 SOM yüklenen bir şema düzenleme ilk şema gezinmesine adımdır. Bir şema düzenlemeyi denemeden önce SOM API kullanarak bir şema geçiş ile biliyor olmanız gerekir. Sonrası-schema-derleme-bilgi (PSCI) öncesi ve sonrası schema derleme özellikleriyle tanıyor olmalıdır.  
  
## <a name="editing-an-xml-schema"></a>Bir XML şeması düzenleme  
 Bu bölümde, iki kod örnekleri sağlanır, her ikisi de oluşturulan müşteri şema düzenleme [yapı XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) konu. İlk örnek kod yeni bir ekler `PhoneNumber` öğesine `Customer` öğesi ikinci kod örneği ekler ve yeni bir `Title` özniteliğini `FirstName` öğesi. İlk örnek de sonrası-schema-derleme kullanır <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu ikinci kod örneğinde sırasında müşteri şeması geçiş aracı olarak kullanır öncesi-schema-derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.  
  
### <a name="phonenumber-element-example"></a>PhoneNumber öğe örneği  
 Bu ilk örnek kod yeni bir ekler `PhoneNumber` öğesine `Customer` müşteri şemasının öğesidir. Kod örneği, aşağıdaki adımlarda müşteri şeması düzenler.  
  
1.  Müşteri şeması yeni bir ekler <xref:System.Xml.Schema.XmlSchemaSet> nesnesi ve ardından derler. Şema doğrulama uyarıları ve okuma veya şema derleme karşılaşılan hataları tarafından işlenen <xref:System.Xml.Schema.ValidationEventHandler> temsilci.  
  
2.  Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği. Sonrası-Schema-derleme-bilgi (PSCI) özellikleri, şema derlendiğinden erişilebilir.  
  
3.  Oluşturur `PhoneNumber` öğesi kullanılarak <xref:System.Xml.Schema.XmlSchemaElement> sınıfı, `xs:string` basit tür kısıtlama kullanarak <xref:System.Xml.Schema.XmlSchemaSimpleType> ve <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> sınıfları, bir desen modeli ekler <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> kısıtlama özelliğini ve ekler kısıtlama için <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> basit tür ve basit tür özelliği <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> , `PhoneNumber` öğesi.  
  
4.  Her tekrarlanan <xref:System.Xml.Schema.XmlSchemaElement> içinde <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> sonrası-schema-derleme koleksiyonu <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu.  
  
5.  Varsa <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> öğesidir `"Customer"`, karmaşık türü alır `Customer` öğesi kullanılarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve kullanarak karmaşık tür dizisi parçacık <xref:System.Xml.Schema.XmlSchemaSequence> sınıfı.  
  
6.  Yeni ekler `PhoneNumber` varolan içeren sırası öğesine `FirstName` ve `LastName` öncesi-schema-derleme kullanarak öğeleri <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> dizisi topluluğu.  
  
7.  Son olarak, yeniden işler ve değiştirilen derler <xref:System.Xml.Schema.XmlSchema> kullanarak nesne <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.  
  
 Tam kod örnek verilmiştir.  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 Oluşturulan değiştirilmiş müşteri şeması aşağıdadır [yapı XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) konu.  
  
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
 İkinci Bu kod örneği, yeni bir ekler `Title` özniteliğini `FirstName` müşteri şemasının öğesidir. İlk kod örneğinde, türü `FirstName` öğesi `xs:string`. İçin `FirstName` dize içerik türü değişti, karmaşık türü bir basit içerik uzantısı içerik modeli ile birlikte bir özniteliği olan öğe.  
  
 Kod örneği, aşağıdaki adımlarda müşteri şeması düzenler.  
  
1.  Müşteri şeması yeni bir ekler <xref:System.Xml.Schema.XmlSchemaSet> nesnesi ve ardından derler. Şema doğrulama uyarıları ve okuma veya şema derleme karşılaşılan hataları tarafından işlenen <xref:System.Xml.Schema.ValidationEventHandler> temsilci.  
  
2.  Derlenmiş alır <xref:System.Xml.Schema.XmlSchema> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet> üzerinde yineleme tarafından <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği. Sonrası-Schema-derleme-bilgi (PSCI) özellikleri, şema derlendiğinden erişilebilir.  
  
3.  Yeni karmaşık tür için oluşturur `FirstName` öğesi kullanılarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı.  
  
4.  Yeni basit içerik uzantısı, temel bir tür ile oluşturur `xs:string`kullanarak <xref:System.Xml.Schema.XmlSchemaSimpleContent> ve <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> sınıfları.  
  
5.  Yeni oluşturur `Title` kullanarak öznitelik <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfı ile bir <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> , `xs:string` ve öznitelik basit içerik uzantısı ekler.  
  
6.  Basit içerik uzantısı ve basit içeriğe karmaşık türünün içerik modeli için basit içerik içerik modeli ayarlar.  
  
7.  Yeni karmaşık tür öncesi-schema-derlemeye ekler <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.  
  
8.  Her tekrarlanan <xref:System.Xml.Schema.XmlSchemaObject> derlemedeki öncesi-schema- <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> koleksiyonu.  
  
> [!NOTE]
>  Çünkü `FirstName` öğesi şemada genel öğesi değil, kullanılabilir değil <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> veya <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonları. Kod örneği bulur `FirstName` ilk bulma tarafından öğesi `Customer` öğesi.  
>   
>  İlk örnek kod sonrası-schema-derleme kullanarak şemasını geçiş <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> koleksiyonu. Bu örnekte, öncesi-schema-derleme <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> toplama şema çapraz geçiş için kullanılır. Her iki koleksiyon şemada genel öğelere erişim sunarken üzerinden yineleme <xref:System.Xml.Schema.XmlSchema.Items%2A> koleksiyonu olduğundan daha uzun süren şemadaki tüm genel öğeler üzerinden yineleme gerekir ve herhangi bir PSCI özellik yok. PSCI koleksiyonları (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, vb.) genel öğeleri, öznitelikleri ve türleri ve bunların PSCI özelliklerini doğrudan erişim sağlar.  
  
1.  Varsa <xref:System.Xml.Schema.XmlSchemaObject> bir öğe olan <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> olan `"Customer"`, karmaşık türü alır `Customer` öğesini kullanarak <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı ve kullanarak karmaşık tür dizisi parçacık <xref:System.Xml.Schema.XmlSchemaSequence> sınıfı.  
  
2.  Her tekrarlanan <xref:System.Xml.Schema.XmlSchemaParticle> derlemedeki öncesi-schema- <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> koleksiyonu.  
  
3.  Varsa <xref:System.Xml.Schema.XmlSchemaParticle> bir öğe kimin 's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> olan `"FirstName"`, ayarlar <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> , `FirstName` yeni öğesine `FirstName` karmaşık tür.  
  
4.  Son olarak, yeniden işler ve değiştirilen derler <xref:System.Xml.Schema.XmlSchema> kullanarak nesne <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve konsola yazar.  
  
 Tam kod örnek verilmiştir.  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 Oluşturulan değiştirilmiş müşteri şeması aşağıdadır [yapı XML şemaları](../../../../docs/standard/data/xml/building-xml-schemas.md) konu.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
