---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 70fb2df1d37af23d9ec19932806989ce3329bf3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191586"
---
# <a name="messagelogging"></a>\<messageLogging >
Bu öğe Windows Communication Foundation (WCF) ileti günlüğüne yazma yetenekleri için ayarları tanımlar.  
  
 \<system.ServiceModel>  
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
|`logEntireMessage`|Tüm iletinin (ileti üst bilgisi ve gövdesi) günlüğe kaydedilip kaydedilmeyeceğini belirten bir Boole değeri. Varsayılan `false`, yani yalnızca ileti üst bilgisi kaydedilir. Bu ayar tüm ileti günlüğe kaydetme düzeylerini etkiler (hizmeti, taşıma ve hatalı).|  
|`logMalformedMessages`|Hatalı biçimlendirilmiş iletilerin kaydedilip kaydedilmeyeceğini belirleyen bir Boole değeri. Hatalı biçimlendirilmiş iletilerin değil doğru sayısı `maxMessagesToLog`. Varsayılan, `false` değeridir.|  
|`logMessagesAtServiceLevel`|İletilerin hizmet düzeyinde (önce şifreleme ve taşıma ilişkili dönüşümler) izlenilmeyeceğini belirleyen bir Boole değeri. Varsayılan, `false` değeridir.|  
|`logMessagesAtTransportLevel`|İletileri taşıma düzeyinde izlenilmeyeceğini belirleyen bir Boole değeri. Yapılandırma dosyasında belirtilen herhangi bir filtre uygulanır ve yalnızca filtrelerle eşleşen iletileri izlendiğini. Varsayılan, `false` değeridir.|  
|`maxMessagesToLog`|Günlüğe kaydedilecek ileti sayısı belirten bir pozitif tamsayı. Varsayılan değer 1000'dir.|  
|`maxSizeOfMessageToLog`|Günlüğe kaydedilecek iletinin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı. Sınırından daha büyük iletiler günlüğe kaydedilmez. Bu ayar, tüm izleme düzeylerini etkiler. 262144(0x4000) varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|filtreler|`filters` Öğesi için XPath filtrelerinde koleksiyonunu tutar. Aktarım ileti günlüğe kaydetme etkinleştirildiğinde (`logMessagesAtTransportLevel` olan `true`), yalnızca filtrelerle eşleşen iletileri kaydedilir.<br /><br /> Filtreler yalnızca Aktarım katmanında uygulanır. Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğü filtreler tarafından etkilenmez.<br /><br /> Bu öğe için yalnızca öznitelik `filter`, bir XPathFilterElement olduğu.<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|tanılama|WCF ayarları için çalışma zamanı incelemesi ve denetimi yöneticisi için tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 İletileri günlüğe yığınında üç farklı düzeylerde: hizmeti, taşıma ve hatalı biçimlendirilmiş. Her düzey ayrı olarak etkinleştirilebilir.  
  
 Taşıma ve hizmet düzeyinde özel iletilerini günlüğe kaydetmek için XPath filtrelerinde eklenebilir. Filtre tanımlanmışsa, tüm iletileri günlüğe kaydedilir. Filtreler iletisinin üstbilgilerini uygulanır. Gövde göz ardı edilir. WCF performansını artırmak için ileti gövdesi yok sayar. Filtrelemek istiyorsanız gövdesi içeriğine bağlı olarak, bunu yapan bir filtre ile özel bir dinleyici oluşturabilirsiniz.  
  
 İleti izlemeyi etkinleştirmek için bir izleme dinleyicisi oluşturmak için ihtiyacınız. Dinleyici çalışan herhangi bir dinleyici olabilir <xref:System.Diagnostics> izleme mimarisi. Aşağıdaki örnek, bu tür bir dinleyici oluşturma işlemini gösterir.  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [İleti Günlüğe Kaydetmeyi Yapılandırma](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
