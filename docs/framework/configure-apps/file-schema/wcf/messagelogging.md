---
title: '&lt;messageLogging&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2febd8582ded47827794762bf0fb842c8131666
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagelogginggt"></a>&lt;messageLogging&gt;
Bu öğe, Windows Communication Foundation (WCF) ileti günlüğe kaydetme özellikleri ayarlarını tanımlar.  
  
 \<Sistem. ServiceModel >  
\<Tanılama >  
\<messageLogging >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <messageLogging logEntireMessage="Boolean"  
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
|`logEntireMessage`|Bir Boole değeri (ileti başlığı ve gövde) tüm ileti günlüğe kaydedilip kaydedilmediğini belirtir. Varsayılan değer `false`, yalnızca ileti üstbilgisi başka bir deyişle, günlüğe kaydedilir. Bu ayar, tüm ileti günlüğe kaydetme düzeylerini etkiler (hizmeti, taşıma ve hatalı biçimlendirilmiş).|  
|`logMalformedMessages`|Hatalı biçimlendirilmiş iletileri günlüğe kaydedilip kaydedilmeyeceğini belirler bir Boole değeri. Hatalı biçimlendirilmiş iletilerini değil doğru Say `maxMessagesToLog`. Varsayılan, `false` değeridir.|  
|`logMessagesAtServiceLevel`|İletiler (önce şifreleme ve taşımayla ilgili Dönüşümlerde) hizmeti düzeyinde izlenip izlenmediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`logMessagesAtTransportLevel`|İletileri aktarım düzeyinde izlenip izlenmediğini belirten bir Boole değeri. Yapılandırma dosyasında belirtilen herhangi bir filtre uygulanır ve yalnızca filtrelerle eşleşen iletileri izlenen. Varsayılan, `false` değeridir.|  
|`maxMessagesToLog`|Günlüğe kaydedilecek ileti sayısı üst sınırını belirtir pozitif bir tamsayı. Varsayılan değer 1000'dir.|  
|`maxSizeOfMessageToLog`|Bir ileti günlüğe kaydetmek için bayt cinsinden en büyük boyutunu belirtir pozitif bir tamsayı. Sınırından daha büyük ileti günlüğe kaydedilmez. Bu ayar, tüm izleme düzeylerini etkiler. 262144(0x4000) varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|filtreler|`filters` Öğesi XPath filtreleri koleksiyonunu içerir. Aktarım ileti günlüğe kaydetme etkinleştirildiğinde (`logMessagesAtTransportLevel` olan `true`), yalnızca filtreleri ile eşleşen iletileri kaydedilir.<br /><br /> Filtreler yalnızca Aktarım katmanında uygulanır. Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğe kaydetme, filtreler tarafından etkilenmez.<br /><br /> Bu öğe için yalnızca öznitelik `filter`, bir XPathFilterElement değil.<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|tanılama|Çalışma zamanı İnceleme için WCF ayarlarını ve yönetici için Denetim tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 İletileri yığınında üç farklı düzeylerde kaydediliyor: Hizmet, taşıma ve hatalı biçimlendirilmiş. Her düzey ayrı olarak etkinleştirilebilir.  
  
 XPath filtreleri, taşıma ve hizmet düzeyleri belirli iletilerini günlüğe kaydetmek için eklenebilir. Hiçbir filtre tanımlanmışsa, tüm iletileri günlüğe kaydedilir. Filtreler yalnızca ileti üstbilgilerini uygulanır. Gövde göz ardı edilir. WCF performansını artırmak için ileti gövdesi yok sayar. Filtrelemek istiyorsanız gövdesi içeriğine göre bunu yapan bir filtre ile özel bir dinleyici oluşturabilirsiniz.  
  
 İleti izlemeyi etkinleştirmek için bir izleme dinleyicisi oluşturmanız gerekir. Dinleyici çalışır dinleyicisi olabilir <xref:System.Diagnostics> izleme mimarisi. Aşağıdaki örnek, bu tür bir dinleyici oluşturun gösterilmiştir.  
  
```xml  
<system.diagnostics>  
    <sources>  
          <source name="System.ServiceModel" switchValue="Verbose">  
              <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="ServiceModel Listener" traceOutputOptions="None" />  
               </listeners>  
        </source>  
            <source name="System.ServiceModel.MessageLogging">  
                <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="MessageLogging Listener" traceOutputOptions="None"/>  
               </listeners>  
        </source>  
    </sources>  
     <sharedListeners>  
            <add initializeData="C:\ItProTools\TraceLog.xml"  
                    type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
                    name="ServiceModel Listener"  
                    traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />  
            <add initializeData="C:\ItProTools\MessageLog.log"  
                    type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
                   name="MessageLogging Listener"  
                   traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />  
    </sharedListeners>  
</system.diagnostics>  
```  
  
## <a name="example"></a>Örnek  
  
```xml  
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
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 [İleti günlüğe kaydetmeyi yapılandırma](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
