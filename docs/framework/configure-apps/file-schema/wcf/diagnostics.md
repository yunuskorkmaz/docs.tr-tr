---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 775ec3a4d3dd8709c61fb46155b5085a3343d218
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192275"
---
# \<diagnostics>

`diagnostics`Öğesi, çalışma zamanı incelemesi ve denetimi için bir yönetici tarafından kullanılabilecek ayarları tanımlar.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a>Syntax  
  
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
|EtwProviderId|ETW oturumlarına olayları yazan olay Izleme sağlayıcısı için tanımlayıcıyı belirten bir dize.|  
|performanceCounters|Derleme için performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir. Geçerli değerler şunlardır<br /><br /> -Off: performans sayaçları devre dışı bırakıldı.<br />-Yalnızca ServiceOnly: yalnızca bu hizmetle ilgili performans sayaçları etkindir.<br />-All: performans sayaçları çalışma zamanında görüntülenebilir.<br />-Varsayılan: tek bir performans sayacı örneği _WCF_Admin oluşturulur. Bu örnek, altyapı tarafından kullanılan SQM verilerinin toplanmasını etkinleştirmek için kullanılır. Bu örnek için sayaç değerlerinden hiçbiri güncelleştirilmemiş ve bu nedenle sıfır olarak kalacak. WCF için bir yapılandırma yoksa, bu varsayılan değerdir.|  
|wmiProviderEnabled|Derleme için WMI sağlayıcısının etkin olup olmadığını belirten bir Boolean değer. Kullanıcının Windows Communication Foundation (WCF) İnceleme ve denetim özelliklerine çalışma zamanı erişimi kazanması için WMI sağlayıcısı gerekir. Varsayılan değer: `false`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|Bir hizmet uygulamasının çalışması sırasında uçtan uca izlemenin farklı yönlerini etkinleştirmenizi ve devre dışı bırakmanızı sağlayan bir yapılandırma öğesi.|  
|[\<messageLogging>](messagelogging.md)|WCF ileti günlüğe kaydetme ayarlarını açıklar.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|serviceModel|Tüm WCF yapılandırma öğelerinin kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  

 `diagnostics`Bölümü bir derlemede bulunan tüm hizmetler için tanılama ayarlarını tanımlar. Derlemede yalnızca bir hizmet olmadığı takdirde, hizmet düzeyinde ayrı Tanılama ayarları tanımlamak mümkün değildir. Öznitelikler, bölümün gereksinimlerine göre ayarlanır.  
  
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
