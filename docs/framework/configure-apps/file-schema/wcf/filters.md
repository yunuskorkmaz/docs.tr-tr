---
description: 'Hakkında daha fazla bilgi edinin: <filters>'
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: c66dd07c91e78d1ae6e10790014c3d1b25e5538d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664606"
---
# \<filters>

<span data-ttu-id="b162b-102">`filters`Öğesi, ne tür bir ileti günlüğe kaydedileceğini denetlemek için kullanılan XPath filtreleri koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="b162b-102">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="b162b-103">Filtreler yalnızca tarafından belirtilen aktarım katmanında uygulanır `logMessagesAtTransportLevel` `true` .</span><span class="sxs-lookup"><span data-stu-id="b162b-103">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="b162b-104">Hizmet düzeyi ve hatalı biçimlendirilmiş ileti günlüğe kaydetme, filtrelerle etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="b162b-104">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="b162b-105">Koleksiyona bir filtre eklemek için `add` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b162b-105">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="b162b-106">Bir veya daha fazla filtre tanımlandığında yalnızca filtrelerden en az biriyle eşleşen mesajlar günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="b162b-106">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="b162b-107">Hiçbir filtre tanımlanmamışsa, tüm iletiler geçer.</span><span class="sxs-lookup"><span data-stu-id="b162b-107">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="b162b-108">Filtreler tam XPath söz dizimini destekler ve yapılandırma dosyasında göründükleri sırada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b162b-108">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="b162b-109">Sözdizimi yanlış bir filtre, yapılandırma özel durumuyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="b162b-109">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="b162b-110">Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b162b-110">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="b162b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b162b-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="b162b-112">İleti Günlüğe Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b162b-112">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
