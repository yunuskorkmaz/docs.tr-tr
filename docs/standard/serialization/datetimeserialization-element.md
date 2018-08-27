---
title: '&lt;dateTimeSerialization&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 15fad472288a72a079991f41e6c2859776d78cca
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930093"
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
|dizileştirme mekanizmasını System.xml.Serialization|XML serileştirme denetlemek için üst düzey öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sürümlerinde 1.0, 1.1, 2.0 ve sonraki sürümlerinde bu özelliği ayarlandığında .NET Framework, **yerel**, <xref:System.DateTime> nesneler her zaman yerel saat biçimlendirilmiş. Diğer bir deyişle, yerel saat dilimi bilgilerini her zaman serileştirilmiş verilerle birlikte gelir. Bu özellik kümesine **yerel** .NET Framework'ün önceki sürümlerle uyumluluk sağlamak için.  
  
 Sürüm 2.0 ve bu özellik kümesine sahip sonraki sürümlerinde .NET Framework'ün **gidiş dönüş**, <xref:System.DateTime> nesneler incelenebilen yerel, UTC veya belirtilmeyen bir saat dilimi olup olmadığını belirlemek için. <xref:System.DateTime> Nesneleri sonra bu bilgileri korunur bir şekilde serileştirilmiş. Bu varsayılan davranış ve eski sürümleri framework ile iletişim kuran değil tüm yeni uygulamalar için önerilen davranışı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.DateTime>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [Yapılandırma Dosyası Şeması](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<schemaImporterExtensions > öğesi](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [\<Ekle > öğesi için \<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)  
 [\<System.xml.Serialization > öğesi](../../../docs/standard/serialization/system-xml-serialization-element.md)
