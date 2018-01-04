---
title: "Yapı XML şemaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 72e3d707caf9c5e64c9860a8e79b5e151ce68852
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="building-xml-schemas"></a>Yapı XML şemaları
Sınıflarda <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı World Wide Web Konsorsiyumu (W3C) XML Şeması öneri tanımlanan yapıları eşlemeniz ve XML şemaları bellek içi oluşturmak için kullanılabilir.  
  
## <a name="building-an-xml-schema"></a>Bir XML şeması oluşturma  
 Aşağıdaki kod örneklerinde SOM API müşteri XML Şeması bellek içi oluşturmak için kullanılır.  
  
### <a name="creating-element-and-attributes"></a>Öğe ve öznitelikler oluşturma  
 Kod örnekleri, alt öğeleri, öznitelikleri ve bunların karşılık gelen türlerine ilk olarak, oluşturma şema, alt ve üst düzey öğeleri müşteri oluşturun.  
  
 Aşağıdaki kod örneğinde, `FirstName` ve `LastName` öğeleri yanı sıra `CustomerId` müşteri şeması özniteliği kullanılarak oluşturulan <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> SOM. sınıfları Gelen apart <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> özelliklerini <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> "name" özniteliğinin değerini karşılık sınıfları `<xs:element />` ve `<xs:attribute />` şema tarafından izin verilen tüm diğer özniteliklerle bir XML Şeması öğelerini (`defaultValue`, `fixedValue`, `form`, vb.) karşılık gelen özelliklere sahip <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları.  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Şema türleri oluşturma  
 İçerik öğeleri ve özniteliklerinin kendi türlerine göre tanımlanır. Öğeleri ve öznitelikleri olan türleridir yerleşik şema türlerinden birini oluşturmak için <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları kullanarak yerleşik türü, karşılık gelen tam adı ile ayarlamak <xref:System.Xml.XmlQualifiedName> sınıfı. Kullanıcı tanımlı bir tür öğeleri ve öznitelikleri oluşturmak için yeni bir basit veya karmaşık türü kullanılarak oluşturulur <xref:System.Xml.Schema.XmlSchemaSimpleType> veya <xref:System.Xml.Schema.XmlSchemaComplexType> sınıfı.  
  
> [!NOTE]
>  Öğe veya öznitelik anonim alt Adlandırılmamış Basit veya karmaşık türleri oluşturmak için (yalnızca basit türler uygulamak için öznitelikler) ayarlamak <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> Adlandırılmamış Basit veya karmaşık türü sınıfları yerine <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> veya <xref:System.Xml.Schema.XmlSchemaAttribute> sınıfları.  
  
 XML şemaları izin her ikisi de adsız ve adlandırılmış basit türler diğer basit türler (yerleşik veya kullanıcı tanımlı) kısıtlama yoluyla türetilmesi için veya bir liste veya diğer basit türler birleşimi oluşturulur. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Sınıfı yerleşik kısıtlayarak basit bir tür oluşturmak için kullanılan `xs:string` türü. Aynı zamanda <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> veya <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> liste veya birleşim türleri oluşturmak için sınıflar. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Özelliği, bir basit tür sınırlaması, liste veya birleşim olup olmadığını gösterir.  
  
 Aşağıdaki kod örneğinde, `FirstName` öğenin türü olan yerleşik türü `xs:string`, `LastName` öğenin türü olan bir kısıtlamadır yerleşik türü adlandırılmış bir basit tür `xs:string`, ile bir `MaxLength` 20, model değeri ve `CustomerId` özniteliğin türü olan yerleşik türü `xs:positiveInteger`. `Customer` Öğesidir, parçacık olduğunda dizisi anonim bir karmaşık tür olarak `FirstName` ve `LastName` öğelerini ve özniteliklerini içeren `CustomerId` özniteliği.  
  
> [!NOTE]
>  Aynı zamanda <xref:System.Xml.Schema.XmlSchemaChoice> veya <xref:System.Xml.Schema.XmlSchemaAll> çoğaltmak için karmaşık tür olarak parçacık sınıfları `<xs:choice />` veya `<xs:all />` semantiği.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Oluşturma ve şemaları derleme  
 Bu nokta, alt öğelerini ve özniteliklerini, bunların karşılık gelen türlerine ve üst düzey `Customer` öğesi bellekteki SOM API'si kullanılarak oluşturulmuş. Aşağıdaki kod örneğinde schema öğesi kullanılarak oluşturulan <xref:System.Xml.Schema.XmlSchema> sınıfı üst düzey öğeleri ve türleri eklenir kullanarak <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> özelliği ve tam şeması derlenmiş kullanarak <xref:System.Xml.Schema.XmlSchemaSet> sınıfı ve yazılır Konsolu.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Yöntemi müşteri şemanın XML şeması için kuralları karşı doğrular ve sonrası schema derleme özellikler kullanılabilir hale getirir.  
  
> [!NOTE]
>  SOM API tüm sonrası schema derleme özelliklerinde sonrası-schema-doğrulama-bilgi farklı.  
  
 <xref:System.Xml.Schema.ValidationEventHandler> Eklenen <xref:System.Xml.Schema.XmlSchemaSet> geri çağırma yöntemini çağıran bir temsilci `ValidationCallback` şema doğrulama uyarıları ve hataları işlemek için.  
  
 Tam kod örneği ve konsola yazılan müşteri şeması verilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [XML Şemaları Okuma ve Yazma](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
