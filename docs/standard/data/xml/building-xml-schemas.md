---
title: XML Şemaları Derleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8c8e1b0d9a79ff22f3194e86cd580f3a7e199b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962023"
---
# <a name="building-xml-schemas"></a>XML Şemaları Derleme
<xref:System.Xml.Schema?displayProperty=nameWithType> Ad alanındaki sınıflar, World Wide Web Konsorsiyumu (W3C) XML şeması önerisi içinde tanımlanan yapılara eşlenir ve XML şemaları bellek içinde oluşturmak için kullanılabilir.  
  
## <a name="building-an-xml-schema"></a>XML şeması oluşturma  
 Aşağıdaki kod örneklerinde, SOM API 'SI, bellek içi bir müşteri XML şeması oluşturmak için kullanılır.  
  
### <a name="creating-element-and-attributes"></a>Öğe ve öznitelikler oluşturma  
 Kod örnekleri, aşağıdan yukarıya ait müşteri şemasını oluşturur, alt öğeleri, öznitelikleri ve önce karşılık gelen türlerini ve ardından üst düzey öğeleri oluşturur.  
  
 Aşağıdaki kod `FirstName` örneğinde, ve `CustomerId` `LastName` öğelerinin yanı sıra müşteri şemasının özniteliği de som 'un <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları kullanılarak oluşturulur. <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> BirXML`<xs:attribute />` şeması içindeki `<xs:element />` ve öğelerinin "Name" özniteliğine karşılık gelen ve sınıflarının özelliklerindenayrıolarak,şematarafındanizinverilentümdiğeröznitelikler(<xref:System.Xml.Schema.XmlSchemaElement.Name%2A> `defaultValue` <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAttribute> , ,,vb.),vesınıflarındakarşılıkgelenözellikleresahiptir.`fixedValue` `form`  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Şema türleri oluşturma  
 Öğelerin ve özniteliklerin içeriği türlerine göre tanımlanır. Türleri yerleşik şema türlerinden biri olan öğeler ve <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> öznitelikler oluşturmak için, <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> sınıflarının özelliği, <xref:System.Xml.XmlQualifiedName> sınıfı kullanılarak yerleşik türün karşılık gelen nitelenmiş adı ile ayarlanır. Öğeler ve öznitelikler için Kullanıcı tanımlı bir tür oluşturmak için <xref:System.Xml.Schema.XmlSchemaSimpleType> veya <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı kullanılarak yeni bir basit veya karmaşık tür oluşturulur.  
  
> [!NOTE]
> Bir öğenin veya özniteliğin anonim alt öğeleri olan adlandırılmamış basit veya karmaşık türler oluşturmak için (yalnızca basit türler öznitelikler için geçerlidir), <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> sınıflarının özelliğini adlandırılmamış basit veya karmaşık türe ayarlayın, <xref:System.Xml.Schema.XmlSchemaElement> veya sınıflarının özelliği yerine. <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> <xref:System.Xml.Schema.XmlSchemaAttribute>  
  
 XML şemaları hem anonim hem de adlandırılmış basit türlerin, diğer basit türlerden (yerleşik veya Kullanıcı tanımlı) kısıtlamasıyla türeme veya bir liste veya diğer basit türlerin birleşimi olarak oluşturulması için izin verir. Sınıfı, yerleşik `xs:string` türü kısıtlayarak basit bir tür oluşturmak için kullanılır. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Ayrıca, veya <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> sınıflarını, <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> liste veya birleşim türleri oluşturmak için de kullanabilirsiniz. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Özelliği, bir basit tür kısıtlaması, liste veya birleşim olduğunu gösterir.  
  
 Aşağıdaki kod örneğinde, `FirstName` öğesinin türü yerleşik türdür `xs:string`, `LastName` öğenin türü yerleşik türün `xs:string` `MaxLength` bir kısıtlaması olan adlandırılmış basit bir türdür ve bir model değeri 20 ' dir ve özniteliğin türü yerleşik türdür `xs:positiveInteger`. `CustomerId` Öğesi, parçacık `FirstName` `CustomerId` ve `LastName` öğelerinin dizisi olan ve öznitelikleri özniteliğini içeren anonim bir karmaşık türdür. `Customer`  
  
> [!NOTE]
> Ayrıca, <xref:System.Xml.Schema.XmlSchemaChoice> ya <xref:System.Xml.Schema.XmlSchemaAll> da sınıflarını yinelemek `<xs:choice />` ya `<xs:all />` da semantiği için karmaşık türün parçacık olarak da kullanabilirsiniz.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Şemaları oluşturma ve derleme  
 Bu noktada, alt öğeler ve öznitelikler, karşılık gelen türleri ve en üst düzey `Customer` öğe som API 'si kullanılarak bellek içinde oluşturulmuştur. Aşağıdaki kod örneğinde, şema öğesi <xref:System.Xml.Schema.XmlSchema> sınıfı kullanılarak oluşturulur, en üst düzey öğeler ve türler <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> özelliği kullanılarak buna eklenir ve tam <xref:System.Xml.Schema.XmlSchemaSet> şema sınıfı kullanılarak derlenir ve öğesine yazılır konsola.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Yöntemi, müşteri şemasını bir XML şeması için kurallara göre doğrular ve şema sonrası derleme özelliklerini kullanılabilir hale getirir.  
  
> [!NOTE]
> SOM API 'sindeki tüm şema sonrası derleme özellikleri, şema-doğrulama-bilgi kümesinden farklıdır.  
  
 Öğesine eklenen, <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama uyarılarını ve hatalarını işlemek için geri çağırma `ValidationCallback` yöntemini çağıran bir temsilcisidir. <xref:System.Xml.Schema.XmlSchemaSet>  
  
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

- [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
