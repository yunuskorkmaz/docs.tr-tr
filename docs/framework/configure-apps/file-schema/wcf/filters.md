---
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: e4ce0452cc46a8f29334fa67f51f14b83290b1c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918880"
---
# <a name="filters"></a>\<Filtreler >

Öğesi `filters` , ne tür bir ileti günlüğe kaydedileceğini denetlemek için kullanılan XPath filtreleri koleksiyonunu tutar.

Filtreler yalnızca tarafından `logMessagesAtTransportLevel` `true`belirtilen aktarım katmanında uygulanır. Hizmet düzeyi ve hatalı biçimlendirilmiş ileti günlüğe kaydetme, filtrelerle etkilenmez.

Koleksiyona bir filtre eklemek için `add` anahtar sözcüğünü kullanın. Bir veya daha fazla filtre tanımlandığında yalnızca filtrelerden en az biriyle eşleşen mesajlar günlüğe kaydedilir. Hiçbir filtre tanımlanmamışsa, tüm iletiler geçer.

Filtreler tam XPath söz dizimini destekler ve yapılandırma dosyasında göründükleri sırada uygulanır. Sözdizimi yanlış bir filtre, yapılandırma özel durumuyla sonuçlanır.

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
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [Günlüğe İleti Kaydetmeyi Yapılandırma](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging >](messagelogging.md)
