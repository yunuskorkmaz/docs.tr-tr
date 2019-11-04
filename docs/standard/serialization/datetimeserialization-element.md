---
title: <dateTimeSerialization> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 180a4942dd4b701b56fe4788d5f8cd8607faaedd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459267"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization > öğesi
Serileştirme modu belirler <xref:System.DateTime> nesneleri.  
  
 \<Yapılandırma >  
\<dateTimeSerialization >  
  
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
 .NET Framework sürüm 1,0, 1,1, 2,0 ve sonraki sürümlerinde, bu özellik **Yerel**olarak ayarlandığında <xref:System.DateTime> nesneleri her zaman yerel saat olarak biçimlendirilir. Diğer bir deyişle, yerel saat dilimi bilgilerini her zaman serileştirilmiş verilerle birlikte gelir. .NET Framework eski sürümleriyle uyumluluğu sağlamak için bu özelliği **Yerel** olarak ayarlayın.  
  
 Sürüm 2,0 ' de ve bu özelliği yukarı **dönüş**olarak ayarlanmış .NET Framework sonraki sürümlerinde, <xref:System.DateTime> nesneleri yerel, UTC veya belirtilmeyen bir saat diliminde olup olmadıklarını belirleyecek şekilde incelenir. <xref:System.DateTime> Nesneleri sonra bu bilgileri korunur bir şekilde serileştirilmiş. Bu varsayılan davranış ve eski sürümleri framework ile iletişim kuran değil tüm yeni uygulamalar için önerilen davranışı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Yapılandırma Dosyası Şeması](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<SchemaImporterExtensions > öğesi](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<SchemaImporterExtensions için > öğesi \<ekleyin >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [System. xml. Serialization > öğesi \<](../../../docs/standard/serialization/system-xml-serialization-element.md)
