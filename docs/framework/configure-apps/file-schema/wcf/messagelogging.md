---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: f54028489ec5aa34ae38115d7a582b01b9da92f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931408"
---
# <a name="messagelogging"></a><span data-ttu-id="e29ad-101">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="e29ad-101">\<messageLogging></span></span>
<span data-ttu-id="e29ad-102">Bu öğe Windows Communication Foundation (WCF) ileti günlüğü özelliklerine yönelik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e29ad-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="e29ad-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e29ad-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e29ad-104">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="e29ad-104">\<diagnostic></span></span>  
<span data-ttu-id="e29ad-105">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="e29ad-105">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e29ad-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e29ad-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e29ad-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e29ad-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e29ad-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e29ad-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e29ad-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e29ad-109">Attributes</span></span>  
  
|<span data-ttu-id="e29ad-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e29ad-110">Attribute</span></span>|<span data-ttu-id="e29ad-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e29ad-111">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="e29ad-112">İletinin tamamının (ileti üst bilgisi ve gövdesi) günlüğe kaydedilip kaydedilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e29ad-112">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="e29ad-113">Varsayılan `false`olarak, yalnızca ileti üstbilgisinin günlüğe kaydedildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-113">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="e29ad-114">Bu ayar tüm ileti günlüğü düzeylerini (hizmet, aktarım ve hatalı biçimlendirilmiş) etkiler.</span><span class="sxs-lookup"><span data-stu-id="e29ad-114">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="e29ad-115">Hatalı biçimlendirilmiş iletilerin günlüğe kaydedilip kaydedilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e29ad-115">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="e29ad-116">Hatalı biçimlendirilmiş iletiler, `maxMessagesToLog`öğesine doğru sayılmaz.</span><span class="sxs-lookup"><span data-stu-id="e29ad-116">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="e29ad-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-117">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="e29ad-118">İletilerin hizmet düzeyinde (şifreleme ve aktarımlarla ilgili dönüşümlerden önce) izlenip izlenmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e29ad-118">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="e29ad-119">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-119">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="e29ad-120">İletilerin Aktarım düzeyinde izlenip izlenmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="e29ad-120">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="e29ad-121">Yapılandırma dosyasında belirtilen filtreler uygulanır ve yalnızca filtrelerle eşleşen iletiler izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-121">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="e29ad-122">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-122">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="e29ad-123">Günlüğe kaydedilecek en fazla ileti sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e29ad-123">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="e29ad-124">Varsayılan değer 1000 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-124">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="e29ad-125">Günlüğe kaydedilecek bir iletinin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e29ad-125">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="e29ad-126">Sınırdan daha büyük mesajlar günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="e29ad-126">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="e29ad-127">Bu ayar tüm izleme düzeylerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="e29ad-127">This setting affects all trace levels.</span></span> <span data-ttu-id="e29ad-128">Varsayılan değer 262144 ' dir (0x4000).</span><span class="sxs-lookup"><span data-stu-id="e29ad-128">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e29ad-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e29ad-129">Child Elements</span></span>  
  
|<span data-ttu-id="e29ad-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="e29ad-130">Element</span></span>|<span data-ttu-id="e29ad-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e29ad-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e29ad-132">filtreler</span><span class="sxs-lookup"><span data-stu-id="e29ad-132">filters</span></span>|<span data-ttu-id="e29ad-133">`filters` Öğesi XPath filtreleri koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="e29ad-133">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="e29ad-134">Aktarım iletisi günlüğü etkin olduğunda (`logMessagesAtTransportLevel` yani `true`), yalnızca filtrelerle eşleşen iletiler günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-134">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="e29ad-135">Filtreler yalnızca aktarım katmanında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e29ad-135">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="e29ad-136">Hizmet düzeyi ve hatalı biçimlendirilmiş ileti günlüğe kaydetme, filtrelerle etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="e29ad-136">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="e29ad-137">Bu öğenin `filter`tek özniteliği, bir XPathFilter.</span><span class="sxs-lookup"><span data-stu-id="e29ad-137">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="e29ad-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e29ad-138">Parent Elements</span></span>  
  
|<span data-ttu-id="e29ad-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="e29ad-139">Element</span></span>|<span data-ttu-id="e29ad-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e29ad-140">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e29ad-141">tanılama</span><span class="sxs-lookup"><span data-stu-id="e29ad-141">diagnostics</span></span>|<span data-ttu-id="e29ad-142">Yönetici için çalışma zamanı incelemesi ve denetimi için WCF ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e29ad-142">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e29ad-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e29ad-143">Remarks</span></span>  
 <span data-ttu-id="e29ad-144">İletiler Yığındaki üç farklı düzeye kaydedilir: hizmet, taşıma ve hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="e29ad-144">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="e29ad-145">Her düzey ayrı olarak etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-145">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="e29ad-146">Aktarım ve hizmet düzeylerindeki belirli iletileri günlüğe kaydetmek için XPath filtreleri eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-146">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="e29ad-147">Hiçbir filtre tanımlanmamışsa, tüm iletiler günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-147">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="e29ad-148">Filtreler yalnızca iletinin üst bilgilerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e29ad-148">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="e29ad-149">Gövde yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="e29ad-149">The body is ignored.</span></span> <span data-ttu-id="e29ad-150">WCF, performansı artırmak için ileti gövdesini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="e29ad-150">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="e29ad-151">Gövdenin içeriğine göre filtrelemek istiyorsanız, filtre içeren özel bir dinleyici oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e29ad-151">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="e29ad-152">İleti izlemeyi etkinleştirmek için bir izleme dinleyicisi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-152">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="e29ad-153">Dinleyici, <xref:System.Diagnostics> izleme mimarisiyle birlikte çalışarak herhangi bir dinleyici olabilir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-153">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="e29ad-154">Aşağıdaki örnek, böyle bir dinleyicinin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e29ad-154">The following example demonstrates how to create such a listener.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="e29ad-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="e29ad-155">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e29ad-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e29ad-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="e29ad-157">Günlüğe İleti Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e29ad-157">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
