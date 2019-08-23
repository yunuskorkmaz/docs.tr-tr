---
title: <add> / <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: e7975bea1435abdb77528628e7b96c65a72cbbc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926695"
---
# <a name="add-of-filters"></a>\<\<filtrelerin > ekleyin >
Günlüğe kaydedilecek ileti türünü belirten bir XPath filtresi.  
  
 \<system.ServiceModel>  
\<Tanılama >  
\<messageLogging >  
\<Filtreler >  
\<> Ekle  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|filtre|Bir XPath 1,0 ifadesi tarafından tanımlanan bir XML belgesi üzerinde bir sorgu belirten bir dize. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtreler >](filters.md)|Ne tür bir ileti günlüğe kaydedileceğini denetlemek için kullanılan XPath filtreleri koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Filtreler yalnızca tarafından `logMessagesAtTransportLevel` `true`belirtilen aktarım katmanında uygulanır. Hizmet düzeyi ve hatalı biçimlendirilmiş ileti günlüğe kaydetme, filtrelerle etkilenmez.  
  
 Koleksiyona bir filtre eklemek için `add` anahtar sözcüğünü kullanın. Bir veya daha fazla filtre tanımlandığında yalnızca filtrelerden en az biriyle eşleşen mesajlar günlüğe kaydedilir. Hiçbir filtre tanımlanmamışsa, tüm iletiler geçer.  
  
 Filtreler tam XPath söz dizimini destekler ve yapılandırma dosyasında göründükleri sırada uygulanır. Sözdizimi yanlış bir filtre, yapılandırma özel durumuyla sonuçlanır.  
  
 Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [Günlüğe İleti Kaydetmeyi Yapılandırma](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging >](messagelogging.md)
