---
title: "Şema düğüm türleri ve yapısı çıkarımını yapma için kurallar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f4a50fcd3e3ee56ded97edef08c2ee08f4a7233
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a>Şema düğüm türleri ve yapısı çıkarımını yapma için kurallar
Bu konu, nasıl bir XML Şeması Tanım Dili (XSD) yapısı için bir XML belgesi düğüm türleri şema çıkarım işlemi çevirir açıklar.  
  
## <a name="element-inference-rules"></a>Öğe çıkarım kuralları  
 Bu bölümde öğesi bildirimleri çıkarım kuralları açıklar. Çıkarımı yapılan öğesi bildirimlerinin sekiz yapıları vardır:  
  
1.  Basit türünün öğesi  
  
2.  Boş öğesi  
  
3.  Özniteliklerle boş öğesi  
  
4.  Öznitelikler ve basit içerik olan öğesi  
  
5.  Bir dizi alt öğeleri olan öğesi  
  
6.  Bir dizi alt öğeleri ve öznitelikleri ile öğesi  
  
7.  Bir dizi seçenek alt öğelerini bir öğesiyle  
  
8.  Bir dizi seçenek alt öğeleri ve özniteliklerinin bir öğesiyle  
  
> [!NOTE]
>  Tüm `complexType` bildirimleri anonim türleri olarak sonuçlandı. Çıkarımı yapılan yalnızca genel kök öğe öğedir; diğer tüm öğeler yerel bağlıdır.  
  
 Şema çıkarım işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma şemaları XML belgelerden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
### <a name="simple-typed-element"></a>Basit yazılan öğesi  
 Aşağıdaki tabloda XML girişi gösterilmektedir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi ve oluşturulan XML şeması. Kalın öğesi için basit tür öğesi çıkarımı yapılan şema gösterir.  
  
 Şema çıkarım işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma şemaları XML belgelerden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a>Boş öğesi  
 Aşağıdaki tabloda XML girişi gösterilmektedir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi ve oluşturulan XML şeması. Kalın öğesi boş öğe için çıkarımı yapılan şema gösterir.  
  
 Şema çıkarım işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma şemaları XML belgelerden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a>Özniteliklerle boş öğesi  
 Aşağıdaki tabloda XML girişi gösterilmektedir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi ve oluşturulan XML şeması. Kalın öğeleri boş öğesinin öznitelikleri olan olayla şema göster.  
  
 Şema çıkarım işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma şemaları XML belgelerden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a>Öznitelikler ve basit içerik olan öğesi  
 Aşağıdaki tabloda XML girişi gösterilmektedir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi ve oluşturulan XML şeması. Kalın öğeleri, öznitelikleri ve basit içeriğe sahip bir öğe için çıkarımı yapılan şema göster.  
  
 Şema çıkarım işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma şemaları XML belgelerden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a>Bir dizi alt öğeleri olan öğesi  
 Aşağıdaki tabloda XML girişi gösterilmektedir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi ve oluşturulan XML şeması. Kalın öğeleri bir dizi alt öğeleri olan bir öğe için çıkarımı yapılan şema göster.  
  
> [!NOTE]
>  Bir öğe yalnızca bir alt öğesi olsa bile, yine bir dizi olarak kabul edilir.  
  
 Şema çıkarım işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma şemaları XML belgelerden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a>Bir dizi alt öğeleri ve öznitelikleri ile öğesi  
 Aşağıdaki tabloda XML girişi gösterilmektedir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi ve oluşturulan XML şeması. Kalın öğeleri öğenin alt öğeleri ve özniteliklerinin dizisiyle çıkarımı yapılan şema göster.  
  
> [!NOTE]
>  Bir öğe yalnızca bir alt öğesi olsa bile, yine bir dizi olarak kabul edilir.  
  
 Şema çıkarım işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma şemaları XML belgelerden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a>Bir sıra ve alt öğelerini seçimi olan öğesi  
 Aşağıdaki tabloda XML girişi gösterilmektedir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi ve oluşturulan XML şeması. Kalın öğeleri bir öğe için bir sıra ve alt öğelerini seçimine çıkarımı yapılan şema göster.  
  
> [!NOTE]
>  `maxOccurs` Özniteliği `xs:choice` ayarlanır `"unbounded"` oluşturulursa şemasında.  
  
 Şema çıkarım işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma şemaları XML belgelerden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a>Bir sıra ve alt öğeleri ve özniteliklerinin tercih öğesi  
 Aşağıdaki tabloda XML girişi gösterilmektedir <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> yöntemi ve oluşturulan XML şeması. Kalın öğeleri bir öğe için bir sıra ve alt öğeleri ve özniteliklerinin seçim çıkarımı yapılan şema göster.  
  
> [!NOTE]
>  `maxOccurs` Özniteliği `xs:choice` ayarlanır `"unbounded"` oluşturulursa şemasında.  
  
 Şema çıkarım işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma şemaları XML belgelerden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Şema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a>Öznitelik işleme  
 Yeni bir öznitelik bir düğümde karşılaşıldığında düğümle oluşturulursa tanımını eklendiğinden `use="required"`. Aynı düğümde örneğinde bulunan sonraki açışınızda zaten çıkarımı yapılan raporlarla geçerli örneğini özniteliklerini çıkarım işlem karşılaştırın. Bazı zaten oluşturulursa olanları örneğinde eksikse `use="optional"` özniteliği tanımına eklenir. Yeni öznitelikler, varolan bildirimlerle eklenir `use="optional"`.  
  
### <a name="occurrence-constraints"></a>Geçişi kısıtlamaları  
 Şema çıkarma işlemi sırasında `minOccurs` ve `maxOccurs` öznitelikleri oluşturulur, oluşturulursa bileşenleri değerlere sahip bir şema için `"0"` veya `"1"` ve `"1"` veya `"unbounded"`. Değerleri `"1"` ve `"unbounded"` kullanılan yalnızca değerleri `"0"` ve `"1"` XML belgesi doğrulanamıyor (örneğin, `MinOccurs="0"` doğru bir şekilde bir öğeyi açıklanmamaktadır `minOccurs="1"` kullanılır).  
  
### <a name="mixed-content"></a>Karışık içerik  
 Karışık içerik (öğeleriyle interspersed örneğin metin), bir öğe içeriyorsa `mixed="true"` özniteliği için çıkarılan karmaşık türü tanımı oluşturulur.  
  
## <a name="other-node-type-inference-rules"></a>Diğer düğümü türü çıkarım kuralları  
 Aşağıdaki tabloda, işlem yönergesi, açıklama, varlık başvurusunun, CDATA, belge türü ve ad alanı düğümleri için çıkarım kuralları açıklar.  
  
|Düğüm türü|Çeviri|  
|---------------|-----------------|  
|İşleme yönergesi|Yoksayıldı.|  
|Yorum|Yoksayıldı.|  
|Varlık başvurusu|<xref:System.Xml.Schema.XmlSchemaInference> Sınıfı varlık başvuruları işlemez. Bir XML belgesi varlık başvuruları içeriyorsa, Varlıkları genişleten bir okuyucunun kullanması gerekir. Örneğin, geçirebilirsiniz bir <xref:System.Xml.XmlTextReader> ile <xref:System.Xml.XmlTextReader.EntityHandling%2A> özelliğini <xref:System.Xml.EntityHandling.ExpandEntities> bir parametre olarak. Varlık başvuruları karşılaştı ve okuyucu varlıklar genişletmez, bir özel durum throw olur.|  
|CDATA|Tüm `<![CDATA[ … ]]` bir XML belgesi bölümlerde çıkarımı yapılan olarak `xs:string`.|  
|Belge türü|Yoksayıldı.|  
|Ad Alanları|Yoksayıldı.|  
  
 Şema çıkarım işlemi hakkında daha fazla bilgi için bkz: [çıkarımını yapma şemaları XML belgelerden](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Schema.XmlSchemaInference>  
 [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [XML Şemasından Çıkarım Yapma](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 [XML Belgelerinden Şema Çıkarımı Yapma](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
 [Basit Türlerin Çıkarımını Yapma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
