---
title: '&lt;Tanılama&gt;'
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 0854ce6525fd7c96cf7c19d2c86dadef1b9a53bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747313"
---
# <a name="ltdiagnosticsgt"></a>&lt;Tanılama&gt;
`diagnostics` Öğe, bir yönetici tarafından çalışma zamanı denetleme ve denetimi için kullanılan ayarları tanımlar.  
  
 \<system.ServiceModel>  
\<Tanılama >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>  
  <diagnostics 
      etwProviderId="String"       
      performanceCounters="Off/ServiceOnly/All/Default"              
      wmiProviderEnabled="Boolean" >       
    <endToEndTracing 
        activityTracing="Boolean"  
        messageFlowTracing="Boolean"  
        propagateActivity="Boolean" />  
    <messageLogging 
        logEntireMessage="Boolean"  
        logMalformedMessages="Boolean"  
        logMessagesAtServiceLevel="Boolean"  
        logMessagesAtTransportLevel="Boolean"  
        maxMessagesToLog="Integer"  
        maxSizeOfMessageToLog="Integer" >  
      <filters>  
        <clear />  
      </filters>  
    </messageLogging>  
  </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|etwProviderId|Olayları ETW oturumlarını Yazar olay izleme sağlayıcısı tanımlayıcısı belirten bir dize.|  
|performans sayaçları|Derleme için performans sayaçları etkinleştirilip etkinleştirilmeyeceğini belirtir. Geçerli değerler:<br /><br /> -Kapalı: Performans sayaçları devre dışı bırakıldı.<br />-ServiceOnly: Yalnızca bu hizmetle ilgili performans sayaçları etkinleştirildi.<br />-Tüm: performans sayaçları çalışma zamanında görüntülenebilir.<br />-Varsayılan: Tek bir performans sayacı örneği _WCF_Admin oluşturulur. Bu örnek, altyapısı tarafından kullanılan SQM Veri toplamayı etkinleştirmek için kullanılır. Bu örnek için sayacı değerlerini hiçbiri güncelleştirilir ve bu nedenle sıfırda kalacaktır. Bu, herhangi bir yapılandırma için WCF varsa, varsayılan değerdir.|  
|wmiProviderEnabled|Derleme için WMI sağlayıcısı etkin olup olmadığını belirten bir Boole değeri. WMI sağlayıcısı denetleme ve denetim özelliklerini Windows Communication Foundation (WCF) çalışma zamanı erişmek kullanıcı için gereklidir. Varsayılan, `false` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<endToEndTracing >](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|Etkinleştirme ve devre dışı uçtan uca izleme bir hizmet uygulaması çalışması sırasında farklı yönlerini olanak sağlayan bir yapılandırma öğesi.|  
|[\<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|WCF ileti günlüğe kaydetme ayarlarını açıklar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|ServiceModel|Tüm WCF yapılandırma öğelerinin kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `diagnostics` Bölümü, bir derlemede bulunan tüm hizmetler için tanılama ayarları tanımlar. Derlemede yalnızca bir hizmet olmadıkça hizmet düzeyinde ayrı tanılama ayarlarını tanımlamak olası değil. Öznitelikleri bölüm gereksinimlerine göre ayarlanır.  
  
## <a name="example"></a>Örnek  
  
```xml  
<diagnostics
    wmiProviderEnabled="false"  
    performanceCounters="all">  
  <messageLogging 
      logEntireMessage="true"  
      logMalformedMessages="true"  
      logMessagesAtServiceLevel="true"  
      logMessagesAtTransportLevel="true"  
      maxMessagesToLog="42"  
      maxSizeOfMessageToLog="42">  
    <filters>  
      <clear />  
    </filters>  
  </messageLogging>  
</diagnostics>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>
