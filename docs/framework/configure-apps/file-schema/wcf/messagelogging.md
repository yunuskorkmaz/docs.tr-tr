---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: fd4d678b1e861a47762d8a64f85dcc052a30fe2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204807"
---
# \<messageLogging>

<span data-ttu-id="99ca6-101">Bu öğe Windows Communication Foundation (WCF) ileti günlüğü özelliklerine yönelik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="99ca6-101">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**  
  
## <a name="syntax"></a><span data-ttu-id="99ca6-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="99ca6-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99ca6-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="99ca6-103">Attributes and Elements</span></span>  

 <span data-ttu-id="99ca6-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99ca6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99ca6-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99ca6-105">Attributes</span></span>  
  
|<span data-ttu-id="99ca6-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="99ca6-106">Attribute</span></span>|<span data-ttu-id="99ca6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99ca6-107">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="99ca6-108">İletinin tamamının (ileti üst bilgisi ve gövdesi) günlüğe kaydedilip kaydedilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="99ca6-108">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="99ca6-109">Varsayılan olarak, `false` yalnızca ileti üstbilgisinin günlüğe kaydedildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="99ca6-109">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="99ca6-110">Bu ayar tüm ileti günlüğü düzeylerini (hizmet, aktarım ve hatalı biçimlendirilmiş) etkiler.</span><span class="sxs-lookup"><span data-stu-id="99ca6-110">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="99ca6-111">Hatalı biçimlendirilmiş iletilerin günlüğe kaydedilip kaydedilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="99ca6-111">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="99ca6-112">Hatalı biçimlendirilmiş iletiler, öğesine doğru sayılmaz `maxMessagesToLog` .</span><span class="sxs-lookup"><span data-stu-id="99ca6-112">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="99ca6-113">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="99ca6-113">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="99ca6-114">İletilerin hizmet düzeyinde (şifreleme ve aktarımlarla ilgili dönüşümlerden önce) izlenip izlenmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="99ca6-114">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="99ca6-115">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="99ca6-115">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="99ca6-116">İletilerin Aktarım düzeyinde izlenip izlenmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="99ca6-116">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="99ca6-117">Yapılandırma dosyasında belirtilen filtreler uygulanır ve yalnızca filtrelerle eşleşen iletiler izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="99ca6-117">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="99ca6-118">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="99ca6-118">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="99ca6-119">Günlüğe kaydedilecek en fazla ileti sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="99ca6-119">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="99ca6-120">Varsayılan değer 1000’dir.</span><span class="sxs-lookup"><span data-stu-id="99ca6-120">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="99ca6-121">Günlüğe kaydedilecek bir iletinin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="99ca6-121">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="99ca6-122">Sınırdan daha büyük mesajlar günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="99ca6-122">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="99ca6-123">Bu ayar tüm izleme düzeylerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="99ca6-123">This setting affects all trace levels.</span></span> <span data-ttu-id="99ca6-124">Varsayılan değer 262144 ' dir (0x4000).</span><span class="sxs-lookup"><span data-stu-id="99ca6-124">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99ca6-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="99ca6-125">Child Elements</span></span>  
  
|<span data-ttu-id="99ca6-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="99ca6-126">Element</span></span>|<span data-ttu-id="99ca6-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99ca6-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99ca6-128">filtreler</span><span class="sxs-lookup"><span data-stu-id="99ca6-128">filters</span></span>|<span data-ttu-id="99ca6-129">`filters`Öğesi XPath filtreleri koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="99ca6-129">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="99ca6-130">Aktarım iletisi günlüğü etkin olduğunda ( `logMessagesAtTransportLevel` yani `true` ), yalnızca filtrelerle eşleşen iletiler günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="99ca6-130">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="99ca6-131">Filtreler yalnızca aktarım katmanında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="99ca6-131">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="99ca6-132">Hizmet düzeyi ve hatalı biçimlendirilmiş ileti günlüğe kaydetme, filtrelerle etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="99ca6-132">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="99ca6-133">Bu öğenin tek özniteliği, `filter` bir XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="99ca6-133">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="99ca6-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="99ca6-134">Parent Elements</span></span>  
  
|<span data-ttu-id="99ca6-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="99ca6-135">Element</span></span>|<span data-ttu-id="99ca6-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99ca6-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99ca6-137">tanılama</span><span class="sxs-lookup"><span data-stu-id="99ca6-137">diagnostics</span></span>|<span data-ttu-id="99ca6-138">Yönetici için çalışma zamanı incelemesi ve denetimi için WCF ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="99ca6-138">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99ca6-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99ca6-139">Remarks</span></span>  

 <span data-ttu-id="99ca6-140">İletiler Yığındaki üç farklı düzeye kaydedilir: hizmet, taşıma ve hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="99ca6-140">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="99ca6-141">Her düzey ayrı olarak etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="99ca6-141">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="99ca6-142">Aktarım ve hizmet düzeylerindeki belirli iletileri günlüğe kaydetmek için XPath filtreleri eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="99ca6-142">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="99ca6-143">Hiçbir filtre tanımlanmamışsa, tüm iletiler günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="99ca6-143">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="99ca6-144">Filtreler yalnızca iletinin üst bilgilerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="99ca6-144">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="99ca6-145">Gövde yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="99ca6-145">The body is ignored.</span></span> <span data-ttu-id="99ca6-146">WCF, performansı artırmak için ileti gövdesini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="99ca6-146">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="99ca6-147">Gövdenin içeriğine göre filtrelemek istiyorsanız, filtre içeren özel bir dinleyici oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99ca6-147">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="99ca6-148">İleti izlemeyi etkinleştirmek için bir izleme dinleyicisi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99ca6-148">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="99ca6-149">Dinleyici, izleme mimarisiyle birlikte çalışarak herhangi bir dinleyici olabilir <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="99ca6-149">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="99ca6-150">Aşağıdaki örnek, böyle bir dinleyicinin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="99ca6-150">The following example demonstrates how to create such a listener.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="99ca6-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="99ca6-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99ca6-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99ca6-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="99ca6-153">İleti Günlüğe Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="99ca6-153">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
