---
title: '&lt;messageLogging&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2febd8582ded47827794762bf0fb842c8131666
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagelogginggt"></a><span data-ttu-id="62456-102">&lt;messageLogging&gt;</span><span class="sxs-lookup"><span data-stu-id="62456-102">&lt;messageLogging&gt;</span></span>
<span data-ttu-id="62456-103">Bu öğe, Windows Communication Foundation (WCF) ileti günlüğe kaydetme özellikleri ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62456-103">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="62456-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="62456-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="62456-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="62456-105">\<diagnostic></span></span>  
<span data-ttu-id="62456-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="62456-106">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62456-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62456-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
                    maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
                            <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62456-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="62456-108">Attributes and Elements</span></span>  
 <span data-ttu-id="62456-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62456-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62456-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62456-110">Attributes</span></span>  
  
|<span data-ttu-id="62456-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="62456-111">Attribute</span></span>|<span data-ttu-id="62456-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62456-112">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="62456-113">Bir Boole değeri (ileti başlığı ve gövde) tüm ileti günlüğe kaydedilip kaydedilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="62456-113">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="62456-114">Varsayılan değer `false`, yalnızca ileti üstbilgisi başka bir deyişle, günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="62456-114">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="62456-115">Bu ayar, tüm ileti günlüğe kaydetme düzeylerini etkiler (hizmeti, taşıma ve hatalı biçimlendirilmiş).</span><span class="sxs-lookup"><span data-stu-id="62456-115">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="62456-116">Hatalı biçimlendirilmiş iletileri günlüğe kaydedilip kaydedilmeyeceğini belirler bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="62456-116">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="62456-117">Hatalı biçimlendirilmiş iletilerini değil doğru Say `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="62456-117">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="62456-118">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="62456-118">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="62456-119">İletiler (önce şifreleme ve taşımayla ilgili Dönüşümlerde) hizmeti düzeyinde izlenip izlenmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="62456-119">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="62456-120">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="62456-120">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="62456-121">İletileri aktarım düzeyinde izlenip izlenmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="62456-121">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="62456-122">Yapılandırma dosyasında belirtilen herhangi bir filtre uygulanır ve yalnızca filtrelerle eşleşen iletileri izlenen.</span><span class="sxs-lookup"><span data-stu-id="62456-122">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="62456-123">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="62456-123">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="62456-124">Günlüğe kaydedilecek ileti sayısı üst sınırını belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="62456-124">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="62456-125">Varsayılan değer 1000'dir.</span><span class="sxs-lookup"><span data-stu-id="62456-125">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="62456-126">Bir ileti günlüğe kaydetmek için bayt cinsinden en büyük boyutunu belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="62456-126">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="62456-127">Sınırından daha büyük ileti günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="62456-127">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="62456-128">Bu ayar, tüm izleme düzeylerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="62456-128">This setting affects all trace levels.</span></span> <span data-ttu-id="62456-129">262144(0x4000) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="62456-129">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62456-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="62456-130">Child Elements</span></span>  
  
|<span data-ttu-id="62456-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="62456-131">Element</span></span>|<span data-ttu-id="62456-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62456-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62456-133">filtreler</span><span class="sxs-lookup"><span data-stu-id="62456-133">filters</span></span>|<span data-ttu-id="62456-134">`filters` Öğesi XPath filtreleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="62456-134">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="62456-135">Aktarım ileti günlüğe kaydetme etkinleştirildiğinde (`logMessagesAtTransportLevel` olan `true`), yalnızca filtreleri ile eşleşen iletileri kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="62456-135">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="62456-136">Filtreler yalnızca Aktarım katmanında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="62456-136">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="62456-137">Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğe kaydetme, filtreler tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="62456-137">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="62456-138">Bu öğe için yalnızca öznitelik `filter`, bir XPathFilterElement değil.</span><span class="sxs-lookup"><span data-stu-id="62456-138">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="62456-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="62456-139">Parent Elements</span></span>  
  
|<span data-ttu-id="62456-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="62456-140">Element</span></span>|<span data-ttu-id="62456-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62456-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62456-142">tanılama</span><span class="sxs-lookup"><span data-stu-id="62456-142">diagnostics</span></span>|<span data-ttu-id="62456-143">Çalışma zamanı İnceleme için WCF ayarlarını ve yönetici için Denetim tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62456-143">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62456-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62456-144">Remarks</span></span>  
 <span data-ttu-id="62456-145">İletileri yığınında üç farklı düzeylerde kaydediliyor: Hizmet, taşıma ve hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="62456-145">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="62456-146">Her düzey ayrı olarak etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="62456-146">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="62456-147">XPath filtreleri, taşıma ve hizmet düzeyleri belirli iletilerini günlüğe kaydetmek için eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="62456-147">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="62456-148">Hiçbir filtre tanımlanmışsa, tüm iletileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="62456-148">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="62456-149">Filtreler yalnızca ileti üstbilgilerini uygulanır.</span><span class="sxs-lookup"><span data-stu-id="62456-149">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="62456-150">Gövde göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="62456-150">The body is ignored.</span></span> <span data-ttu-id="62456-151">WCF performansını artırmak için ileti gövdesi yok sayar.</span><span class="sxs-lookup"><span data-stu-id="62456-151">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="62456-152">Filtrelemek istiyorsanız gövdesi içeriğine göre bunu yapan bir filtre ile özel bir dinleyici oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62456-152">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="62456-153">İleti izlemeyi etkinleştirmek için bir izleme dinleyicisi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62456-153">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="62456-154">Dinleyici çalışır dinleyicisi olabilir <xref:System.Diagnostics> izleme mimarisi.</span><span class="sxs-lookup"><span data-stu-id="62456-154">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="62456-155">Aşağıdaki örnek, bu tür bir dinleyici oluşturun gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="62456-155">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
          <source name="System.ServiceModel" switchValue="Verbose">  
              <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="ServiceModel Listener" traceOutputOptions="None" />  
               </listeners>  
        </source>  
            <source name="System.ServiceModel.MessageLogging">  
                <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="MessageLogging Listener" traceOutputOptions="None"/>  
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
  
## <a name="example"></a><span data-ttu-id="62456-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="62456-156">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62456-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62456-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 [<span data-ttu-id="62456-158">İleti günlüğe kaydetmeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="62456-158">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
