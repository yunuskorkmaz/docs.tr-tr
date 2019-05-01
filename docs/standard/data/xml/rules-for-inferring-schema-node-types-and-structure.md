---
title: Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c2f28490203bcc4853bc6736ce7089f308bc275
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027049"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a>Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları
Bu konu nasıl bir XML belgesi bir XML Şeması Tanım Dili (XSD) yapısını düğüm türleri şema çıkarımı işleminin çevirir açıklar.  
  
## <a name="element-inference-rules"></a>Öğe çıkarım kuralları  
 Bu bölümde öğesi bildirimleri için çıkarım kuralları açıklar. Çıkarımı yapılan öğesi bildirimlerinin sekiz yapıları vardır:  
  
1. Basit Tür öğesi  
  
2. Boş öğe  
  
3. Boş bir öğe öznitelikleri  
  
4. Öznitelikler ve basit içerik olan öğe  
  
5. Alt öğeleri dizi olan öğe  
  
6. Öğesi ile bir dizi alt öğeler ve öznitelikler  
  
7. Öğesi ile bir dizi alt öğelerin seçenekleri  
  
8. Alt öğeler ve öznitelikler seçeneklerden bir dizi öğe  
  
> [!NOTE]
>  Tüm `complexType` bildirimleri anonim türleri olarak sonuçlandı. Çıkarımı yapılan yalnızca genel öğesi kök öğesidir; diğer tüm öğeleri yereldir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma XML belgelerinden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
### <a name="simple-typed-element"></a>Basit türü belirtilmiş öğesi  
 Aşağıdaki tablo XML giriş gösterir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi yanı sıra, oluşturulan XML şeması. Çıkarımı yapılan basit bir tür öğe için şema kalın öğeyi gösterir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma XML belgelerinden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a>Boş öğe  
 Aşağıdaki tablo XML giriş gösterir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi yanı sıra, oluşturulan XML şeması. Kalın öğesi boş öğe için çıkarsanan şema gösterir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma XML belgelerinden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a>Boş bir öğe öznitelikleri  
 Aşağıdaki tablo XML giriş gösterir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi yanı sıra, oluşturulan XML şeması. Boş bir öğe öznitelikleri için çıkarsanan şema kalın öğeleri gösterir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma XML belgelerinden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a>Öznitelikler ve basit içerik olan öğe  
 Aşağıdaki tablo XML giriş gösterir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi yanı sıra, oluşturulan XML şeması. Kalın öğeleri, öznitelikleri ve basit içeriğe sahip bir öğe için çıkarsanan şema gösterir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma XML belgelerinden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a>Alt öğeleri dizi olan öğe  
 Aşağıdaki tablo XML giriş gösterir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi yanı sıra, oluşturulan XML şeması. Kalın öğeleri alt öğeleri dizi olan bir öğe için çıkarsanan şema gösterir.  
  
> [!NOTE]
>  Öğe yalnızca bir alt öğe olsa bile, yine de bir dizi olarak değerlendirilir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma XML belgelerinden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a>Öğesi ile bir dizi alt öğeler ve öznitelikler  
 Aşağıdaki tablo XML giriş gösterir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi yanı sıra, oluşturulan XML şeması. Alt öğeler ve öznitelikler dizisi olan bir öğe için çıkarsanan şema kalın öğeleri gösterir.  
  
> [!NOTE]
>  Öğe yalnızca bir alt öğe olsa bile, yine de bir dizi olarak değerlendirilir.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma XML belgelerinden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a>Öğe dizisi ve alt öğelerini seçenekleri  
 Aşağıdaki tablo XML giriş gösterir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi yanı sıra, oluşturulan XML şeması. Bir öğe için bir sequence ve choice alt öğelerin ile sonuçlandı. şema kalın öğeleri gösterir.  
  
> [!NOTE]
>  `maxOccurs` Özniteliği `xs:choice` ayarlanır `"unbounded"` çıkarsanan şema.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma XML belgelerinden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a>Öğe dizisi ve alt öğeler ve öznitelikler seçimi  
 Aşağıdaki tablo XML giriş gösterir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi yanı sıra, oluşturulan XML şeması. Bir öğe için bir sequence ve choice alt öğeleri ve özniteliklerinin ile sonuçlandı. şema kalın öğeleri gösterir.  
  
> [!NOTE]
>  `maxOccurs` Özniteliği `xs:choice` ayarlanır `"unbounded"` çıkarsanan şema.  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma XML belgelerinden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a>Öznitelik işleme  
 Yeni bir öznitelik içinde bir düğüm karşılaşıldığında, düğümle çıkarsanan tanımı eklenir `use="required"`. Aynı düğümde örneğinde bulunan sonraki açışınızda zaten çıkarılan oluşturduklarıyla öznitelikleri geçerli örneğin çıkarımı işleminin karşılaştırın. Zaten gösterilen olanları bazıları örneğinde eksikse `use="optional"` özniteliği tanımına eklenir. Yeni öznitelikler, mevcut bildirimlerle eklenir `use="optional"`.  
  
### <a name="occurrence-constraints"></a>Örnek kısıtlamaları  
 Şema çıkarımı işlemi sırasında `minOccurs` ve `maxOccurs` öznitelikleri oluşturulur, çıkarsanan değerlere sahip bir şema bileşenleri için `"0"` veya `"1"` ve `"1"` veya `"unbounded"`. Değerleri `"1"` ve `"unbounded"` kullanılan yalnızca değerleri `"0"` ve `"1"` XML belgesi doğrulanamıyor (örneğin, `MinOccurs="0"` doğru bir şekilde bir öğe açıklamaz `minOccurs="1"` kullanılır).  
  
### <a name="mixed-content"></a>Karışık içerik  
 Karışık içerik (öğeleri ile interspersed örneğin metin), bir öğe içeriyorsa `mixed="true"` özniteliği çıkarılan karmaşık türü tanımı oluşturulur.  
  
## <a name="other-node-type-inference-rules"></a>Diğer düğümü türü çıkarım kuralları  
 Aşağıdaki tabloda, işlem yönergesi, yorum, varlık başvurusu, CDATA, belge türü ve ad alanı düğümleri için çıkarım kuralları açıklar.  
  
|Düğüm türü|Çeviri|  
|---------------|-----------------|  
|İşleme yönergesi|Yoksayıldı.|  
|Yorum|Yoksayıldı.|  
|Varlık başvurusu|<xref:System.Xml.Schema.XmlSchemaInference> Sınıfı varlık başvurularını işlemiyor. Bir XML belgesi varlık başvuruları içeriyorsa, Varlıkları genişleten bir okuyucu kullanmanız gerekir. Örneğin, geçirebilirsiniz bir <xref:System.Xml.XmlTextReader> ile <xref:System.Xml.XmlTextReader.EntityHandling%2A> özelliğini <xref:System.Xml.EntityHandling.ExpandEntities> bir parametre olarak. Varlık başvuruları karşılaştı ve okuyucu varlıkları genişletmeyen bir özel durum throw ' dir.|  
|CDATA|Tüm `<![CDATA[ … ]]` bir XML belgesi bölümlerine nelze odvodit olarak `xs:string`.|  
|Belge türü|Yoksayıldı.|  
|Ad Alanları|Yoksayıldı.|  
  
 Şema çıkarımı işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma XML belgelerinden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaInference>
- [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [XML Şemasından Çıkarım Yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [XML Belgelerinden Şema Çıkarımı Yapma](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)
- [Basit Türlerin Çıkarımını Yapma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
