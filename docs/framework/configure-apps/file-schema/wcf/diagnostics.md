---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 3fc7828d399555f7c459f6dd067ce9a24b8998b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704069"
---
# <a name="diagnostics"></a>\<Tanılama >
`diagnostics` Öğesi, bir yönetici tarafından çalışma zamanı incelemesi ve denetimi için kullanılan ayarları tanımlar.  
  
 \<system.ServiceModel>  
\<Tanılama >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
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
|etwProviderId|ETW oturumlarına olayları yazan Olay İzleyici sağlayıcısı için tanımlayıcıyı belirleyen bir dize.|  
|PerformanceCounters|Derleme için performans sayaçlarının etkin olup olmadığını belirtir. Geçerli değerler:<br /><br /> -Kapalı: Performans sayaçları devre dışı bırakıldı.<br />-ServiceOnly: Yalnızca bu hizmetle ilgili performans sayaçları etkindir.<br />-Tüm: Performans sayaçları, çalışma zamanında görüntülenebilir.<br />-Varsayılan: Tek performans sayacı örneği _WCF_Admin oluşturulur. Bu örnek, altyapısı tarafından kullanılan SQM Veri toplamayı etkinleştirmek için kullanılır. Bu örneğin sayacı değerlerini hiçbiri güncelleştirilir ve bu nedenle sıfırdan kalacaktır. WCF için yapılandırma varsa varsayılan değer budur.|  
|wmiProviderEnabled|Derleme için WMI sağlayıcısı etkin olup olmadığını belirten bir Boole değeri. WMI sağlayıcısı, çalışma zamanı incelemesi ve denetimi özellikleri Windows Communication Foundation (WCF) erişmek kullanıcı için gereklidir. Varsayılan, `false` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<endToEndTracing >](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|Enable ve disable uçtan uca izleme hizmet uygulamasının çalışması sırasında farklı yönlerini olanak tanıyan bir yapılandırma öğesi.|  
|[\<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|WCF iletileri günlüğe kaydetme ayarlarını açıklar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|serviceModel|Tüm WCF yapılandırma öğelerinin kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 `diagnostics` Bölümü, bir derlemede bulunan tüm hizmetler için tanılama ayarları tanımlar. Derlemede yalnızca bir hizmet olmadığı sürece hizmet düzeyinde ayrı tanılama ayarları tanımlamak mümkün değildir. Öznitelikleri bölüm gereksinimlerine göre ayarlanır.  
  
## <a name="example"></a>Örnek  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
