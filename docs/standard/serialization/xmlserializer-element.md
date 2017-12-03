---
title: "&lt;xmlSerializer&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17e4fcd1b471a5197f2e6a30bad10cbdbe22f216
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltxmlserializergt-element"></a>&lt;xmlSerializer&gt; öğesi
Belirtir ilerleme durumunu ek bir denetim olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> yapılır.  
  
 \<Yapılandırma >  
\<dizileştirme mekanizmasını System.xml.Serialization >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**checkDeserializeAdvances**|Belirtir olup olmadığını ilerleme durumunu <xref:System.Xml.Serialization.XmlSerializer> denetlenir. Özniteliği "true" veya "false" olarak ayarlayın. Varsayılan değer "true" ise.|  
|**useLegacySerializationGeneration**|Belirtir olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> C# kod bir dosyaya yazmak ve sonra da bir derlemeye derlemek tarafından derlemeleri oluşturan eski serileştirme oluşturma kullanır. Varsayılan değer **false**.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dizileştirme mekanizmasını System.xml.Serialization > öğesi](../../../docs/standard/serialization/system-xml-serialization-element.md)|İçin yapılandırma ayarlarını içeren <xref:System.Xml.Serialization.XmlSerializer> ve <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfları.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, <xref:System.Xml.Serialization.XmlSerializer> güvenilmeyen verileri işlenirken ek bir olası hizmet reddi saldırılarına karşı güvenliği katmanı sağlar. Bunu seri durumundan çıkarma sırasında sonsuz döngü algılamak deneyerek yapar. Bir koşul algılanırsa, aşağıdaki iletisiyle bir özel durum: "İç hata: temel alınan akışta seri durumdan çıkarma başarısız oldu."  
  
 Bu iletiyi alan değil gerekmeyen gösteren bir saldırı hizmet reddi devam ediyor. Bazı ender durumlarda, yanlış Pozitif sonsuz döngü algılama mekanizması oluşturur ve yasal gelen ileti için özel durum. Belirli uygulamanızda bu ek koruma katmanı tarafından yasal iletileri reddediliyor bulursanız, ayarlamak **checkDeserializeAdvances** özniteliği "false".  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod **checkDeserializeAdvances** özniteliği "false".  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [\<dizileştirme mekanizmasını System.xml.Serialization > öğesi](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [XML ve SOAP seri hale getirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)
