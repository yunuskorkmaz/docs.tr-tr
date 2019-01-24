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
# <a name="ltfiltersgt"></a><span data-ttu-id="d6d08-102">&lt;Filtreleri&gt;</span><span class="sxs-lookup"><span data-stu-id="d6d08-102">&lt;filters&gt;</span></span>

<span data-ttu-id="d6d08-103">`filters` Öğesi hangi tür iletilerin günlüğe denetlemek için kullanılan XPath filtrelerinin bir koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="d6d08-103">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="d6d08-104">Filtreler yalnızca Aktarım katmanında, tarafından belirtilen uygulanır `logMessagesAtTransportLevel` olduğu `true`.</span><span class="sxs-lookup"><span data-stu-id="d6d08-104">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="d6d08-105">Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğü filtreler tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="d6d08-105">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="d6d08-106">Koleksiyona bir filtre eklemek için `add` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d6d08-106">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="d6d08-107">Bir veya daha fazla filtre tanımlandığında, en az bir filtre ile eşleşen iletileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="d6d08-107">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="d6d08-108">Filtre boş tanımlıysa, tüm iletileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="d6d08-108">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="d6d08-109">Filtreler XPath tamamını destekler ve yapılandırma dosyasında göründükleri sırayla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d6d08-109">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="d6d08-110">Sözdizimsel olarak yanlış bir filtre yapılandırma bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="d6d08-110">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="d6d08-111">Yalnızca bir SOAP üst bilgisi bölümü olan iletiler kaydeden filtre yapılandırmak nasıl bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d6d08-111">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6d08-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6d08-112">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="d6d08-113">Günlüğe İleti Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d6d08-113">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="d6d08-114">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="d6d08-114">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
