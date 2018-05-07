---
title: '&lt;dateTimeSerialization&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 5e48753b5e8383a1ad946a29636e30ef07ceee9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ltdatetimeserializationgt-element"></a>&lt;dateTimeSerialization&gt; öğesi
Serileştirme modu belirler <xref:System.DateTime> nesneleri.  
  
 \<Yapılandırma >  
\<dateTimeSerialization >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelikler|Açıklama|  
|----------------|-----------------|  
|`mode`|İsteğe bağlı. Serileştirme modunu belirtir. Birine ayarlayın <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> değerleri. Varsayılan değer **gidiş dönüş**.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|dizileştirme mekanizmasını System.xml.Serialization|XML serileştirme denetleme en üst düzey öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sürümlerinde 1.0, 1.1, bu özellik ayarlandığında, .NET Framework 2.0 ve sonraki sürümleri **yerel**, <xref:System.DateTime> nesneler her zaman yerel zaman olarak biçimlendirilmiş. Diğer bir deyişle, yerel saat dilimi bilgilerini her zaman serileştirilmiş verilerle birlikte gelir. Bu özelliği ayarlamak **yerel** .NET Framework'ün daha eski sürümleriyle uyumluluk sağlamak için.  
  
 Sürüm 2.0 ve .NET Framework'ün bu özellik kümesine sahip sonraki sürümlerde **gidiş dönüş**, <xref:System.DateTime> nesneleri incelenmesini yerel, UTC veya belirtilmeyen bir saat dilimi olup olmadıklarını belirlemek için. <xref:System.DateTime> Nesneleri sonra bu bilgileri korunur bir şekilde serileştirilmiş. Bu varsayılan davranış ve eski sürümleri framework ile iletişim kuran değil tüm yeni uygulamalar için önerilen davranışı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.DateTime>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [Yapılandırma Dosyası Şeması](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<schemaImporterExtensions > öğesi](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [\<Ekle > öğesi için \<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [\<dizileştirme mekanizmasını System.xml.Serialization > öğesi](../../../docs/standard/serialization/system-xml-serialization-element.md)
