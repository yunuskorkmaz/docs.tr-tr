---
title: '&lt;Filtreleri&gt;'
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: 5f50b1ad4abfa77022a17d6497b614721382ec1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600199"
---
# <a name="ltfiltersgt"></a>&lt;Filtreleri&gt;

`filters` Öğesi hangi tür iletilerin günlüğe denetlemek için kullanılan XPath filtrelerinin bir koleksiyonunu tutar.

Filtreler yalnızca Aktarım katmanında, tarafından belirtilen uygulanır `logMessagesAtTransportLevel` olduğu `true`. Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğü filtreler tarafından etkilenmez.

Koleksiyona bir filtre eklemek için `add` anahtar sözcüğü. Bir veya daha fazla filtre tanımlandığında, en az bir filtre ile eşleşen iletileri günlüğe kaydedilir. Filtre boş tanımlıysa, tüm iletileri geçirir.

Filtreler XPath tamamını destekler ve yapılandırma dosyasında göründükleri sırayla uygulanır. Sözdizimsel olarak yanlış bir filtre yapılandırma bir özel durum oluşur.

Yalnızca bir SOAP üst bilgisi bölümü olan iletiler kaydeden filtre yapılandırmak nasıl bir örnek verilmiştir.
  
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
- [Günlüğe İleti Kaydetmeyi Yapılandırma](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
