---
title: XML şemaları derleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10b2471d13d410826cec3404725117649442297b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43885707"
---
# <a name="building-xml-schemas"></a>XML şemaları derleme
Sınıflarda <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı, World Wide Web Consortium (W3C) XML Şeması öneri de tanımlanan yapıları eşlemeniz ve XML şemaları bellek içi derleme için kullanılabilir.  
  
## <a name="building-an-xml-schema"></a>Bir XML şeması oluşturma  
 İzleyen kod örneklerinde SOM API XML şema bellek içi müşteri oluşturmak için kullanılır.  
  
### <a name="creating-element-and-attributes"></a>Öğe ve öznitelikler oluşturma  
 Kod örnekleri, müşteri alt öğeleri, öznitelikleri ve bunların karşılık gelen türlerine ilk olarak, oluşturma şema, alt ve üst düzey öğeleri oluşturun.  
  
 Aşağıdaki kod örneğinde, `FirstName` ve `LastName` öğeleri yanı sıra `CustomerId` müşteri şema özniteliği kullanılarak oluşturulur <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> SOM. sınıfları Gelen apart <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> özelliklerini <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> için "name" özniteliğinin değerini karşılık gelen sınıflar `<xs:element />` ve `<xs:attribute />` öğeleri bir XML Şeması şema tarafından izin verilen tüm öznitelikler (`defaultValue`, `fixedValue`, `form`, vb.) karşılık gelen özelliklere sahip <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları.  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Şema türleri oluşturma  
 İçerik öğeleri ve özniteliklerinin, bunların türleri tarafından tanımlanır. Öğeler ve öznitelikler eşleşen türleri, bir yerleşik şema türleri oluşturmak için <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları kullanarak yerleşik tür karşılık gelen tam adı ile ayarlanır <xref:System.Xml.XmlQualifiedName> sınıfı. Öğeler ve öznitelikler için kullanıcı tanımlı bir tür oluşturmak için yeni bir basit veya karmaşık türü kullanılarak oluşturulan <xref:System.Xml.Schema.XmlSchemaSimpleType> veya <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı.  
  
> [!NOTE]
>  Anonim alt öğesi olan bir öğe veya öznitelik adsız basit veya karmaşık türleri oluşturmak için (yalnızca basit türler için öznitelikleri uygulanır), ayarlama <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> adsız basit veya karmaşık tür için sınıflar yerine <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları.  
  
 XML şemaları izin hem anonim ve adlandırılmış basit türler (yerleşik veya kullanıcı tanımlı) basit diğer türlerden kısıtlama türetilen veya bir liste veya diğer basit tür UNION olarak oluşturulur. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Yerleşik kısıtlayarak basit bir tür oluşturmak için kullanılan sınıf `xs:string` türü. Ayrıca <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> veya <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> listesi veya birleşim türleri oluşturmak için sınıf. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Özelliği, bir basit türü kısıtlaması, liste veya birleşim olup olmadığını gösterir.  
  
 Aşağıdaki kod örneğinde, `FirstName` öğenin türü, yerleşik tür `xs:string`, `LastName` öğenin türü, bir yerleşik tür kısıtlaması adlandırılmış bir basit tür `xs:string`, ile bir `MaxLength` model değeri 20'li ve `CustomerId` öznitelik türü yerleşik türüdür `xs:positiveInteger`. `Customer` Öğedir, parçacık dizisi olan anonim bir karmaşık tür, `FirstName` ve `LastName` öğelerini ve özniteliklerini içeren `CustomerId` özniteliği.  
  
> [!NOTE]
>  Ayrıca <xref:System.Xml.Schema.XmlSchemaChoice> veya <xref:System.Xml.Schema.XmlSchemaAll> sınıfları parçacık olarak çoğaltmak için karmaşık türün `<xs:choice />` veya `<xs:all />` semantiği.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Oluşturma ve şemaları derlenirken  
 Bu nokta, alt öğeleri ve öznitelikleri, bunların karşılık gelen türlerine ve üst düzey `Customer` öğesi bellek içi SOM API'si kullanılarak oluşturuldu. Aşağıdaki kod örneğinde şema öğesi kullanılarak oluşturulan <xref:System.Xml.Schema.XmlSchema> sınıfı, üst düzey öğeleri ve türleri eklenir kullanarak <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> özelliği ve tam şeması derlendiği kullanarak <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve yazılan Konsolu.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Yöntemi müşteri şeması bir XML şeması için kuralları karşı doğrular ve sonrası schema derleme özellikler kullanılabilir hale getirir.  
  
> [!NOTE]
>  Tüm sonrası schema derleme özellikleri SOM API'sindeki sonrası-schema-doğrulama-bilgi kümesi farklı.  
  
 <xref:System.Xml.Schema.ValidationEventHandler> Eklenen <xref:System.Xml.Schema.XmlSchemaSet> geri çağırma yöntemi çağıran bir temsilci `ValidationCallback` şema doğrulama uyarıları ve hataları işlemek için.  
  
 Tam kod örneği ve konsoluna yazılan müşteri şeması verilmiştir.  
  
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
