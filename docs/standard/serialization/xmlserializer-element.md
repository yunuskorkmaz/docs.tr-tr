---
title: '&lt;xmlSerializer&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 2770b82f71f3c4b43df4c44f75248e5392c528c2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178474"
---
# <a name="ltxmlserializergt-element"></a>&lt;xmlSerializer&gt; öğesi
Belirtir ilerleme durumunu ek bir denetim olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> yapılır.  
  
 \<Yapılandırma >  
\<System.xml.Serialization >  
  
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
|[\<System.xml.Serialization > öğesi](../../../docs/standard/serialization/system-xml-serialization-element.md)|İçin yapılandırma ayarlarını içeren <xref:System.Xml.Serialization.XmlSerializer> ve <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfları.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, <xref:System.Xml.Serialization.XmlSerializer> güvenilmeyen verileri işlenirken bir ek güvenlik olası hizmet reddi saldırılarını karşı katmanı sağlar. Bunu seri durumundan çıkarma sırasında sonsuz döngü algılamak deneyerek yapar. Bir koşul algılanırsa, aşağıdaki iletisiyle bir özel durum: "İç hata: temel alınan akışta seri kaldırma başarısız oldu."  
  
 Bu iletiyi alan değil gerekmeyen gösteren bir saldırı hizmet reddi devam ediyor. Bazı ender durumlarda, yanlış Pozitif sonsuz döngü algılama mekanizması oluşturur ve yasal gelen ileti için özel durum. Belirli uygulamanızda bu ek koruma katmanı tarafından yasal iletileri reddediliyor bulursanız ayarlamak **checkDeserializeAdvances** "false" özniteliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod **checkDeserializeAdvances** "false" özniteliği.  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Serialization.XmlSerializer>  
- [\<System.xml.Serialization > öğesi](../../../docs/standard/serialization/system-xml-serialization-element.md)  
- [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)
