---
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: e4ce0452cc46a8f29334fa67f51f14b83290b1c8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69918880"
---
# \<filters>

<span data-ttu-id="4823b-101">`filters`Öğesi, ne tür bir ileti günlüğe kaydedileceğini denetlemek için kullanılan XPath filtreleri koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="4823b-101">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="4823b-102">Filtreler yalnızca tarafından belirtilen aktarım katmanında uygulanır `logMessagesAtTransportLevel` `true` .</span><span class="sxs-lookup"><span data-stu-id="4823b-102">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="4823b-103">Hizmet düzeyi ve hatalı biçimlendirilmiş ileti günlüğe kaydetme, filtrelerle etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="4823b-103">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="4823b-104">Koleksiyona bir filtre eklemek için `add` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="4823b-104">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="4823b-105">Bir veya daha fazla filtre tanımlandığında yalnızca filtrelerden en az biriyle eşleşen mesajlar günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4823b-105">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="4823b-106">Hiçbir filtre tanımlanmamışsa, tüm iletiler geçer.</span><span class="sxs-lookup"><span data-stu-id="4823b-106">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="4823b-107">Filtreler tam XPath söz dizimini destekler ve yapılandırma dosyasında göründükleri sırada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4823b-107">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="4823b-108">Sözdizimi yanlış bir filtre, yapılandırma özel durumuyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="4823b-108">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="4823b-109">Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4823b-109">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="4823b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4823b-110">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="4823b-111">İleti Günlüğe Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4823b-111">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
