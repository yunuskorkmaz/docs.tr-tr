---
title: <dateTimeSerialization> Öğesi
description: Bu makalede <dateTimeSerialization> , DateTime nesnelerinin serileştirme modunu belirleyen öğesi açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289648"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization> Öğesi
Serileştirme modu belirler <xref:System.DateTime> nesneleri.  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelikler|Açıklama|  
|----------------|-----------------|  
|`mode`|İsteğe bağlı. Serileştirme modunu belirtir. Birine ayarlayın <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> değerleri. Varsayılan **gidiş dönüş**'dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|dizileştirme mekanizmasını System.xml.Serialization|XML serileştirmesini denetlemek için en üst düzey öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 1,0, 1,1, 2,0 ve sonraki sürümlerinde, bu özellik **Yerel**olarak ayarlandığında <xref:System.DateTime> nesneler her zaman yerel saat olarak biçimlendirilir. Diğer bir deyişle, yerel saat dilimi bilgilerini her zaman serileştirilmiş verilerle birlikte gelir. .NET Framework eski sürümleriyle uyumluluğu sağlamak için bu özelliği **Yerel** olarak ayarlayın.  
  
 Sürüm 2,0 ' de ve bu özelliğe sahip .NET Framework sonraki sürümlerinde, yukarı **dönüş**olarak ayarlanan <xref:System.DateTime> nesneler, yerel, UTC veya belirtilmeyen bir saat diliminde olup olmadıklarını belirleyecek şekilde incelenir. <xref:System.DateTime> Nesneleri sonra bu bilgileri korunur bir şekilde serileştirilmiş. Bu varsayılan davranış ve eski sürümleri framework ile iletişim kuran değil tüm yeni uygulamalar için önerilen davranışı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions>Dosyalarında](schemaimporterextensions-element.md)
- [\<add>İçin öğesi\<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization>Dosyalarında](system-xml-serialization-element.md)
