---
title: <xmlSerializer> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: b83ecda30bba8af1f3175eb6ad08593b07a80e6c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249545"
---
# <a name="xmlserializer-element"></a>\<xmlSerializer> Elemanı
Belirtir ilerleme durumunu ek bir denetim olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> yapılır.  
  
 \<yapılandırma>  
\<system.xml.serialization>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**kontrolDeserializeAvanslar**|Belirtir olup olmadığını ilerleme durumunu <xref:System.Xml.Serialization.XmlSerializer> denetlenir. Özniteliği "true" veya "false" olarak ayarlayın. Varsayılan "true"dur.|  
|**useLegacySerializationGeneration**|Belirtir olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> C# kod bir dosyaya yazmak ve sonra da bir derlemeye derlemek tarafından derlemeleri oluşturan eski serileştirme oluşturma kullanır. Varsayılan **yanlıştır.**|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.xml.serialization> Elemanı](../../../docs/standard/serialization/system-xml-serialization-element.md)|İçin yapılandırma ayarlarını içeren <xref:System.Xml.Serialization.XmlSerializer> ve <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfları.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, <xref:System.Xml.Serialization.XmlSerializer> güvenilmeyen verileri deserializing hizmet reddi olası reddi saldırılarına karşı ek bir güvenlik katmanı sağlar. Bunu seri durumundan çıkarma sırasında sonsuz döngü algılamak deneyerek yapar. Böyle bir durum algılanırsa, bir özel durum şu iletiyle atılır: "İç hata: deserialization altta yatan akış üzerinde ilerlemek için başarısız oldu."  
  
 Bu iletiyi alan değil gerekmeyen gösteren bir saldırı hizmet reddi devam ediyor. Bazı ender durumlarda, yanlış Pozitif sonsuz döngü algılama mekanizması oluşturur ve yasal gelen ileti için özel durum. Özel uygulamanızda meşru iletilerin bu ekstra koruma katmanı tarafından reddedildiğini fark ederseniz, "false" olarak **denetleDeserializeAdvances** özniteliği ni ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, "false" özniteliğini **deserializeAdvances** olarak ayarlar.  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Serialization.XmlSerializer>
- [\<system.xml.serialization> Elemanı](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)
