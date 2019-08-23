---
title: Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c68cd98b496143e6b964383f8fa0c3af5d2c87d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939637"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a>Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları
Bu konuda, şema çıkarımı işleminin bir XML belgesindeki düğüm türlerini bir XML şeması tanım dili (XSD) yapısına nasıl dönüştürdüğünde açıklanmaktadır.  
  
## <a name="element-inference-rules"></a>Öğe çıkarım kuralları  
 Bu bölümde, öğe bildirimleri için çıkarım kuralları açıklanmaktadır. Çıkarsanmayacak öğe bildirimlerinin sekiz yapısı vardır:  
  
1. Basit türdeki öğe  
  
2. Boş öğe  
  
3. Öznitelikleri olan boş öğe  
  
4. Öznitelikleri ve basit içeriği olan öğe  
  
5. Alt öğeleri dizisi olan öğe  
  
6. Alt öğeler ve öznitelikler dizisi olan öğe  
  
7. Alt öğelerin seçim dizisine sahip öğe  
  
8. Alt öğe ve özniteliklerin bir dizi seçimi olan öğe  
  
> [!NOTE]
> Tüm `complexType` bildirimler anonim türler olarak algılanır. Çıkarılan tek genel öğe kök öğesidir; diğer tüm öğeler yereldir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)yapma.  
  
### <a name="simple-typed-element"></a>Basit tür belirtilmiş öğe  
 Aşağıdaki tabloda, <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemine XML girişi ve oluşturulan XML şeması gösterilmektedir. Kalın öğe, basit tür öğesi için gösterilen şemayı gösterir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)yapma.  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a>Boş öğe  
 Aşağıdaki tabloda, <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemine XML girişi ve oluşturulan XML şeması gösterilmektedir. Kalın öğe, boş öğe için gösterilen şemayı gösterir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)yapma.  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a>Öznitelikleri olan boş öğe  
 Aşağıdaki tabloda, <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemine XML girişi ve oluşturulan XML şeması gösterilmektedir. Kalın öğeler, özniteliklerin bulunduğu boş öğe için gösterilen şemayı gösterir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)yapma.  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a>Öznitelikleri ve basit Içeriği olan öğe  
 Aşağıdaki tabloda, <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemine XML girişi ve oluşturulan XML şeması gösterilmektedir. Kalın öğeler, öznitelikleri ve basit içeriği olan bir öğe için gösterilen şemayı gösterir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)yapma.  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a>Alt öğeleri dizisi olan öğe  
 Aşağıdaki tabloda, <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemine XML girişi ve oluşturulan XML şeması gösterilmektedir. Kalın öğeler, alt öğeleri dizisi olan bir öğe için gösterilen şemayı gösterir.  
  
> [!NOTE]
> Bir öğenin yalnızca bir alt öğesi olsa bile, yine de bir sıra olarak kabul edilir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)yapma.  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a>Alt öğeler ve öznitelikler dizisi olan öğe  
 Aşağıdaki tabloda, <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemine XML girişi ve oluşturulan XML şeması gösterilmektedir. Kalın öğeler, alt öğe ve özniteliklerin sırası olan bir öğe için gösterilen şemayı gösterir.  
  
> [!NOTE]
> Bir öğenin yalnızca bir alt öğesi olsa bile, yine de bir sıra olarak kabul edilir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)yapma.  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a>Alt öğelerin sırası ve seçimlerine sahip öğe  
 Aşağıdaki tabloda, <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemine XML girişi ve oluşturulan XML şeması gösterilmektedir. Kalın öğeler, bir öğe için gösterilen şemayı bir dizi ve tercih edilen alt öğeleri gösterir.  
  
> [!NOTE]
> Öğesinin özniteliği, gösterilen şemada olarak `"unbounded"` ayarlanır. `maxOccurs` `xs:choice`  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)yapma.  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a>Alt öğe ve özniteliklerin sırası ve seçimi içeren öğe  
 Aşağıdaki tabloda, <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemine XML girişi ve oluşturulan XML şeması gösterilmektedir. Kalın öğeler, alt öğe ve özniteliklerin sırası ve seçimi içeren bir öğe için gösterilen şemayı gösterir.  
  
> [!NOTE]
> Öğesinin özniteliği, gösterilen şemada olarak `"unbounded"` ayarlanır. `maxOccurs` `xs:choice`  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)yapma.  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a>Öznitelik Işleme  
 Düğüm içinde yeni bir özniteliğe her karşılaşıldığında, bu, ile `use="required"`düğümün çıkarılan tanımına eklenir. Örnekte aynı düğüm bir sonraki sefer olduğunda, çıkarım işlemi geçerli örneğin özniteliklerini zaten çıkartılan olanlarla karşılaştıracaktır. Örnekte zaten başka bir görünenler varsa, `use="optional"` öznitelik tanımına eklenir. Yeni öznitelikler ile `use="optional"`var olan bildirimlere eklenir.  
  
### <a name="occurrence-constraints"></a>Oluşum kısıtlamaları  
 `minOccurs` Şema çıkarımı işlemi sırasında, ve `maxOccurs` öznitelikleri, bir şemanın Çıkarsanan bileşenleri için, veya `"1"` ve `"1"` ya `"unbounded"`da değerleri `"0"` oluşturulur. `"1"` Değerler `minOccurs="1"` `MinOccurs="0"` ve `"unbounded"` yalnızca değerler`"0"` ve`"1"` XML belgesini doğrulayamıyorsa kullanılır (örneğin, bir öğeyi doğru bir şekilde açıklamıyorsa, kullanılır).  
  
### <a name="mixed-content"></a>Karışık Içerik  
 Bir öğe, karışık içerik içeriyorsa (örneğin, öğelerle birlikte metin oluşturma), `mixed="true"` bu öznitelik, gösterilen karmaşık tür tanımı için oluşturulur.  
  
## <a name="other-node-type-inference-rules"></a>Diğer düğüm türü çıkarımı kuralları  
 Aşağıdaki tabloda yönerge, açıklama, varlık başvurusu, CDATA, belge türü ve ad alanı düğümlerini işlemek için çıkarım kuralları açıklanmaktadır.  
  
|Düğüm türü|Çeviri|  
|---------------|-----------------|  
|İşlem yönergesi|LIP.|  
|Yorum|LIP.|  
|Varlık başvurusu|Sınıf <xref:System.Xml.Schema.XmlSchemaInference> , varlık başvurularını işlemez. Bir XML belgesi varlık başvuruları içeriyorsa, varlıkları genişleten bir okuyucu kullanmanız gerekir. Örneğin, <xref:System.Xml.XmlTextReader.EntityHandling%2A> özelliğini bir parametre olarak ayarlanmış <xref:System.Xml.XmlTextReader> şekilde <xref:System.Xml.EntityHandling.ExpandEntities> bir ile geçirebilirsiniz. Varlık başvurularına karşılaşılırsa ve okuyucu varlıkları genişletmezse bir özel durum oluşturur.|  
|CDATA|XML `<![CDATA[ … ]]` belgesindeki tüm bölümler, olarak `xs:string`algılanır.|  
|Belge türü|LIP.|  
|Ad Alanları|LIP.|  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz. [xml belgelerinden şemaları esnek](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)yapma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaInference>
- [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [XML Şemasından Çıkarım Yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [XML Belgelerinden Şema Çıkarımı Yapma](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)
- [Basit Türlerin Çıkarımını Yapma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
