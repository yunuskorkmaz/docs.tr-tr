---
title: '&lt;filtrelerin&gt; &lt;eklenmesi&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff083cfbcdfa772bb5904f4311d95e399c22c97e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltfiltersgt"></a>&lt;filtrelerin&gt; &lt;eklenmesi&gt;
Günlüğe kaydedilecek ileti türünü belirten bir XPath filtre.  
  
 \<Sistem. ServiceModel >  
\<Tanılama >  
\<messageLogging >  
\<filtreleri >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<filters>  
   <add filter="String"/>  
</filters>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|filtre|Bir XPath 1.0 ifade tarafından tanımlanan bir XML belgesi üzerinde bir sorgu belirten bir dize. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filtreleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|Ne tür bir ileti günlüğe denetlemek için kullanılan XPath filtreleri koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tarafından belirtilen yalnızca Aktarım katmanında, filtrelerin uygulandığı `logMessagesAtTransportLevel` olan `true`. Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğe kaydetme, filtreler tarafından etkilenmez.  
  
 Koleksiyona bir filtre eklemek için kullanın `add` anahtar sözcüğü. Bir veya daha fazla filtre tanımlandığında, en az bir filtre ile eşleşen iletileri günlüğe kaydedilir. Hiçbir filtre tanımlanmış olması durumunda, tüm iletileri geçirir.  
  
 Filtreler tam XPath sözdizimini desteklemek ve yapılandırma dosyasında göründükleri sırada uygulanır. Sözdizimsel olarak yanlış bir filtre yapılandırma istisnası ile sonuçlanır.  
  
 SOAP üstbilgi bölümü olan iletiler kaydeden filtreyi yapılandırmak nasıl bir örnek verilmiştir.  
  
## <a name="example"></a>Örnek  
 SOAP üstbilgi bölümü olan iletiler kaydeden filtreyi yapılandırmak nasıl bir örnek verilmiştir.  
  
```xml  
<messageLogging logEntireMessage="true"  
     logMalformedMessages="true" logMessagesAtServiceLevel="true"  
     logMessagesAtTransportLevel="true" maxMessagesToLog="420">  
     <filters>  
        <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                        /soap:Envelope/soap:Headers  
        </add>  
     </filters>  
</messageLogging>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [İleti günlüğe kaydetmeyi yapılandırma](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [İleti günlüğe kaydetmeyi yapılandırma](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [\<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
