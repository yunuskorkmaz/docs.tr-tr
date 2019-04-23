---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 70fb2df1d37af23d9ec19932806989ce3329bf3c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191586"
---
# <a name="messagelogging"></a><span data-ttu-id="64ffc-101">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="64ffc-101">\<messageLogging></span></span>
<span data-ttu-id="64ffc-102">Bu öğe Windows Communication Foundation (WCF) ileti günlüğüne yazma yetenekleri için ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64ffc-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="64ffc-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="64ffc-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="64ffc-104">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="64ffc-104">\<diagnostic></span></span>  
<span data-ttu-id="64ffc-105">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="64ffc-105">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ffc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64ffc-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64ffc-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="64ffc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="64ffc-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64ffc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64ffc-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="64ffc-109">Attributes</span></span>  
  
|<span data-ttu-id="64ffc-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="64ffc-110">Attribute</span></span>|<span data-ttu-id="64ffc-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ffc-111">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="64ffc-112">Tüm iletinin (ileti üst bilgisi ve gövdesi) günlüğe kaydedilip kaydedilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="64ffc-112">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="64ffc-113">Varsayılan `false`, yani yalnızca ileti üst bilgisi kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-113">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="64ffc-114">Bu ayar tüm ileti günlüğe kaydetme düzeylerini etkiler (hizmeti, taşıma ve hatalı).</span><span class="sxs-lookup"><span data-stu-id="64ffc-114">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="64ffc-115">Hatalı biçimlendirilmiş iletilerin kaydedilip kaydedilmeyeceğini belirleyen bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="64ffc-115">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="64ffc-116">Hatalı biçimlendirilmiş iletilerin değil doğru sayısı `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="64ffc-116">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="64ffc-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-117">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="64ffc-118">İletilerin hizmet düzeyinde (önce şifreleme ve taşıma ilişkili dönüşümler) izlenilmeyeceğini belirleyen bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="64ffc-118">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="64ffc-119">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-119">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="64ffc-120">İletileri taşıma düzeyinde izlenilmeyeceğini belirleyen bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="64ffc-120">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="64ffc-121">Yapılandırma dosyasında belirtilen herhangi bir filtre uygulanır ve yalnızca filtrelerle eşleşen iletileri izlendiğini.</span><span class="sxs-lookup"><span data-stu-id="64ffc-121">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="64ffc-122">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-122">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="64ffc-123">Günlüğe kaydedilecek ileti sayısı belirten bir pozitif tamsayı.</span><span class="sxs-lookup"><span data-stu-id="64ffc-123">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="64ffc-124">Varsayılan değer 1000'dir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-124">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="64ffc-125">Günlüğe kaydedilecek iletinin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="64ffc-125">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="64ffc-126">Sınırından daha büyük iletiler günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="64ffc-126">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="64ffc-127">Bu ayar, tüm izleme düzeylerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="64ffc-127">This setting affects all trace levels.</span></span> <span data-ttu-id="64ffc-128">262144(0x4000) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="64ffc-128">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64ffc-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="64ffc-129">Child Elements</span></span>  
  
|<span data-ttu-id="64ffc-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="64ffc-130">Element</span></span>|<span data-ttu-id="64ffc-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ffc-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64ffc-132">filtreler</span><span class="sxs-lookup"><span data-stu-id="64ffc-132">filters</span></span>|<span data-ttu-id="64ffc-133">`filters` Öğesi için XPath filtrelerinde koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="64ffc-133">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="64ffc-134">Aktarım ileti günlüğe kaydetme etkinleştirildiğinde (`logMessagesAtTransportLevel` olan `true`), yalnızca filtrelerle eşleşen iletileri kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-134">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="64ffc-135">Filtreler yalnızca Aktarım katmanında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="64ffc-135">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="64ffc-136">Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğü filtreler tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="64ffc-136">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="64ffc-137">Bu öğe için yalnızca öznitelik `filter`, bir XPathFilterElement olduğu.</span><span class="sxs-lookup"><span data-stu-id="64ffc-137">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="64ffc-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="64ffc-138">Parent Elements</span></span>  
  
|<span data-ttu-id="64ffc-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="64ffc-139">Element</span></span>|<span data-ttu-id="64ffc-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ffc-140">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64ffc-141">tanılama</span><span class="sxs-lookup"><span data-stu-id="64ffc-141">diagnostics</span></span>|<span data-ttu-id="64ffc-142">WCF ayarları için çalışma zamanı incelemesi ve denetimi yöneticisi için tanımlar.</span><span class="sxs-lookup"><span data-stu-id="64ffc-142">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64ffc-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64ffc-143">Remarks</span></span>  
 <span data-ttu-id="64ffc-144">İletileri günlüğe yığınında üç farklı düzeylerde: hizmeti, taşıma ve hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="64ffc-144">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="64ffc-145">Her düzey ayrı olarak etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-145">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="64ffc-146">Taşıma ve hizmet düzeyinde özel iletilerini günlüğe kaydetmek için XPath filtrelerinde eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-146">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="64ffc-147">Filtre tanımlanmışsa, tüm iletileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-147">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="64ffc-148">Filtreler iletisinin üstbilgilerini uygulanır.</span><span class="sxs-lookup"><span data-stu-id="64ffc-148">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="64ffc-149">Gövde göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-149">The body is ignored.</span></span> <span data-ttu-id="64ffc-150">WCF performansını artırmak için ileti gövdesi yok sayar.</span><span class="sxs-lookup"><span data-stu-id="64ffc-150">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="64ffc-151">Filtrelemek istiyorsanız gövdesi içeriğine bağlı olarak, bunu yapan bir filtre ile özel bir dinleyici oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64ffc-151">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="64ffc-152">İleti izlemeyi etkinleştirmek için bir izleme dinleyicisi oluşturmak için ihtiyacınız.</span><span class="sxs-lookup"><span data-stu-id="64ffc-152">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="64ffc-153">Dinleyici çalışan herhangi bir dinleyici olabilir <xref:System.Diagnostics> izleme mimarisi.</span><span class="sxs-lookup"><span data-stu-id="64ffc-153">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="64ffc-154">Aşağıdaki örnek, bu tür bir dinleyici oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="64ffc-154">The following example demonstrates how to create such a listener.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="64ffc-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="64ffc-155">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64ffc-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64ffc-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="64ffc-157">Günlüğe İleti Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="64ffc-157">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
