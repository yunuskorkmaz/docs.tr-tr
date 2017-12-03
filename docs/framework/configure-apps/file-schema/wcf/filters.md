---
title: '&lt;filtreleri&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb8588f9699f44c584fa075e2d1e994c27f0c527
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltersgt"></a>&lt;filtreleri&gt;

`filters` Öğesi ne tür bir ileti günlüğe denetlemek için kullanılan XPath filtreleri koleksiyonunu içerir.

Tarafından belirtilen yalnızca Aktarım katmanında, filtrelerin uygulandığı `logMessagesAtTransportLevel` olan `true`. Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğe kaydetme, filtreler tarafından etkilenmez.

Koleksiyona bir filtre eklemek için kullanın `add` anahtar sözcüğü. Bir veya daha fazla filtre tanımlandığında, en az bir filtre ile eşleşen iletileri günlüğe kaydedilir. Hiçbir filtre tanımlanmış olması durumunda, tüm iletileri geçirir.

Filtreler tam XPath sözdizimini desteklemek ve yapılandırma dosyasında göründükleri sırada uygulanır. Sözdizimsel olarak yanlış bir filtre yapılandırma istisnası ile sonuçlanır.

SOAP üstbilgi bölümü olan iletiler kaydeden filtreyi yapılandırmak nasıl bir örnek verilmiştir.

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

 <xref:System.ServiceModel.Configuration.DiagnosticSection><xref:System.ServiceModel.Diagnostics> <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> <xref:System.ServiceModel.Configuration.MessageLoggingElement> <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A> <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection> <xref:System.ServiceModel.Configuration.XPathMessageFilterElement> <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> [Yapılandırma ileti günlüğe kaydetme](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [ \<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
