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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 21f2115f83772312e1b9f42a66c53ba8ee2834f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltersgt"></a><span data-ttu-id="2824f-102">&lt;filtreleri&gt;</span><span class="sxs-lookup"><span data-stu-id="2824f-102">&lt;filters&gt;</span></span>

<span data-ttu-id="2824f-103">`filters` Öğesi ne tür bir ileti günlüğe denetlemek için kullanılan XPath filtreleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="2824f-103">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="2824f-104">Tarafından belirtilen yalnızca Aktarım katmanında, filtrelerin uygulandığı `logMessagesAtTransportLevel` olan `true`.</span><span class="sxs-lookup"><span data-stu-id="2824f-104">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="2824f-105">Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğe kaydetme, filtreler tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="2824f-105">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="2824f-106">Koleksiyona bir filtre eklemek için kullanın `add` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2824f-106">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="2824f-107">Bir veya daha fazla filtre tanımlandığında, en az bir filtre ile eşleşen iletileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2824f-107">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="2824f-108">Hiçbir filtre tanımlanmış olması durumunda, tüm iletileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="2824f-108">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="2824f-109">Filtreler tam XPath sözdizimini desteklemek ve yapılandırma dosyasında göründükleri sırada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2824f-109">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="2824f-110">Sözdizimsel olarak yanlış bir filtre yapılandırma istisnası ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="2824f-110">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="2824f-111">SOAP üstbilgi bölümü olan iletiler kaydeden filtreyi yapılandırmak nasıl bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2824f-111">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2824f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2824f-112">See also</span></span>

 <span data-ttu-id="2824f-113"><xref:System.ServiceModel.Configuration.DiagnosticSection><xref:System.ServiceModel.Diagnostics> <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> <xref:System.ServiceModel.Configuration.MessageLoggingElement> <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A> <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection> <xref:System.ServiceModel.Configuration.XPathMessageFilterElement> <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> [Yapılandırma ileti günlüğe kaydetme](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [ \<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="2824f-113"><xref:System.ServiceModel.Configuration.DiagnosticSection> <xref:System.ServiceModel.Diagnostics> <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> <xref:System.ServiceModel.Configuration.MessageLoggingElement> <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A> <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection> <xref:System.ServiceModel.Configuration.XPathMessageFilterElement> <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> [Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [\<messageLogging>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)</span></span>
