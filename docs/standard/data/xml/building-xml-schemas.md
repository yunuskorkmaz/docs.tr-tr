---
title: XML Şemaları Derleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: adc1a10bb9acb14ee88589c13e28c49773e42100
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291597"
---
# <a name="building-xml-schemas"></a>XML Şemaları Derleme
Ad alanındaki sınıflar, <xref:System.Xml.Schema?displayProperty=nameWithType> World Wide Web Konsorsiyumu (W3C) XML şeması önerisi içinde tanımlanan yapılara eşlenir ve XML şemaları bellek içinde oluşturmak için kullanılabilir.  
  
## <a name="building-an-xml-schema"></a>XML şeması oluşturma  
 Aşağıdaki kod örneklerinde, SOM API 'SI, bellek içi bir müşteri XML şeması oluşturmak için kullanılır.  
  
### <a name="creating-element-and-attributes"></a>Öğe ve öznitelikler oluşturma  
 Kod örnekleri, aşağıdan yukarıya ait müşteri şemasını oluşturur, alt öğeleri, öznitelikleri ve önce karşılık gelen türlerini ve ardından üst düzey öğeleri oluşturur.  
  
 Aşağıdaki kod örneğinde, `FirstName` ve `LastName` öğelerinin yanı sıra `CustomerId` Müşteri ŞEMASıNıN özniteliği de <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> som 'un ve sınıfları kullanılarak oluşturulur. <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> Bir XML şeması içindeki ve öğelerinin "Name" özniteliğine karşılık gelen ve sınıflarının özelliklerinden ayrı `<xs:element />` `<xs:attribute />` olarak, şemanın (,, vb.) izin verdiği tüm diğer özniteliklerin `defaultValue` `fixedValue` `form` ve sınıflarında karşılık gelen özellikleri vardır <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> .  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Şema türleri oluşturma  
 Öğelerin ve özniteliklerin içeriği türlerine göre tanımlanır. Türleri yerleşik şema türlerinden biri olan öğeler ve öznitelikler oluşturmak için, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> <xref:System.Xml.Schema.XmlSchemaElement> veya sınıflarının özelliği, <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfı kullanılarak yerleşik türün karşılık gelen nitelenmiş adı ile ayarlanır <xref:System.Xml.XmlQualifiedName> . Öğeler ve öznitelikler için Kullanıcı tanımlı bir tür oluşturmak için veya sınıfı kullanılarak yeni bir basit veya karmaşık tür oluşturulur <xref:System.Xml.Schema.XmlSchemaSimpleType> <xref:System.Xml.Schema.XmlSchemaComplexType> .  
  
> [!NOTE]
> Bir öğenin veya özniteliğin anonim alt öğeleri olan adlandırılmamış basit veya karmaşık türler oluşturmak için (yalnızca basit türler öznitelikler için geçerlidir), veya sınıflarının özelliğini <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> veya sınıflarının özelliği yerine adlandırılmamış basit veya karmaşık tür olarak ayarlayın <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> .  
  
 XML şemaları hem anonim hem de adlandırılmış basit türlerin, diğer basit türlerden (yerleşik veya Kullanıcı tanımlı) kısıtlamasıyla türeme veya bir liste veya diğer basit türlerin birleşimi olarak oluşturulması için izin verir. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction>Sınıfı, yerleşik türü kısıtlayarak basit bir tür oluşturmak için kullanılır `xs:string` . Ayrıca, <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> veya <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> sınıflarını, liste veya birleşim türleri oluşturmak için de kullanabilirsiniz. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType>Özelliği, bir basit tür kısıtlaması, liste veya birleşim olduğunu gösterir.  
  
 Aşağıdaki kod örneğinde, `FirstName` öğesinin türü yerleşik türdür `xs:string` , `LastName` öğenin türü yerleşik türün kısıtlaması olan adlandırılmış basit bir türdür, bir `xs:string` `MaxLength` model değeri 20 ' dir ve `CustomerId` özniteliğin türü yerleşik bir türdür `xs:positiveInteger` ... `Customer`Öğesi, parçacık `FirstName` ve öğelerinin dizisi olan `LastName` ve öznitelikleri özniteliğini içeren anonim bir karmaşık türdür `CustomerId` .  
  
> [!NOTE]
> Ayrıca, <xref:System.Xml.Schema.XmlSchemaChoice> ya da <xref:System.Xml.Schema.XmlSchemaAll> sınıflarını yinelemek ya da semantiği için karmaşık türün parçacık olarak da kullanabilirsiniz `<xs:choice />` `<xs:all />` .  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Şemaları oluşturma ve derleme  
 Bu noktada, alt öğeler ve öznitelikler, karşılık gelen türleri ve en üst düzey `Customer` öğe som API 'si kullanılarak bellek içinde oluşturulmuştur. Aşağıdaki kod örneğinde, şema öğesi sınıfı kullanılarak oluşturulur <xref:System.Xml.Schema.XmlSchema> , en üst düzey öğeler ve türler özelliği kullanılarak buna eklenir <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> ve tam şema sınıfı kullanılarak derlenir <xref:System.Xml.Schema.XmlSchemaSet> ve konsola yazılır.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType>Yöntemi, müşteri şemasını BIR XML şeması için kurallara göre doğrular ve şema sonrası derleme özelliklerini kullanılabilir hale getirir.  
  
> [!NOTE]
> SOM API 'sindeki tüm şema sonrası derleme özellikleri, şema-doğrulama-bilgi kümesinden farklıdır.  
  
 <xref:System.Xml.Schema.ValidationEventHandler>Öğesine eklenen, <xref:System.Xml.Schema.XmlSchemaSet> `ValidationCallback` şema doğrulama uyarılarını ve hatalarını işlemek için geri çağırma yöntemini çağıran bir temsilcisidir.  
  
 Aşağıdaki kod örneği ve konsola yazılan müşteri şeması aşağıda verilmiştir.  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
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
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](xml-schema-object-model-overview.md)
- [XML Şemaları Okuma ve Yazma](reading-and-writing-xml-schemas.md)
- [XML Şemalarını Çapraz Geçirme](traversing-xml-schemas.md)
- [XML Şemalarını Düzenleme](editing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](post-schema-compilation-infoset.md)
