---
title: '&lt;filtrelerin&gt; &lt;eklenmesi&gt;'
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 2a26a94c01fdb04b8a9e2d381a28cc909bbdac8f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754616"
---
# <a name="ltaddgt-of-ltfiltersgt"></a><span data-ttu-id="adc82-102">&lt;filtrelerin&gt; &lt;eklenmesi&gt;</span><span class="sxs-lookup"><span data-stu-id="adc82-102">&lt;add&gt; of &lt;filters&gt;</span></span>
<span data-ttu-id="adc82-103">Günlüğe kaydedilecek ileti türünü belirten bir XPath filtre.</span><span class="sxs-lookup"><span data-stu-id="adc82-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="adc82-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="adc82-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="adc82-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="adc82-105">\<diagnostic></span></span>  
<span data-ttu-id="adc82-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="adc82-106">\<messageLogging></span></span>  
<span data-ttu-id="adc82-107">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="adc82-107">\<filters></span></span>  
<span data-ttu-id="adc82-108">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="adc82-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc82-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adc82-109">Syntax</span></span>  
  
```xml  
<filters>  
   <add filter="String"/>  
</filters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adc82-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="adc82-110">Attributes and Elements</span></span>  
 <span data-ttu-id="adc82-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="adc82-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adc82-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="adc82-112">Attributes</span></span>  
  
|<span data-ttu-id="adc82-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="adc82-113">Attribute</span></span>|<span data-ttu-id="adc82-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adc82-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adc82-115">filtre</span><span class="sxs-lookup"><span data-stu-id="adc82-115">filter</span></span>|<span data-ttu-id="adc82-116">Bir XPath 1.0 ifade tarafından tanımlanan bir XML belgesi üzerinde bir sorgu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="adc82-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="adc82-117">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="adc82-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adc82-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="adc82-118">Child Elements</span></span>  
 <span data-ttu-id="adc82-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="adc82-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="adc82-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="adc82-120">Parent Elements</span></span>  
  
|<span data-ttu-id="adc82-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="adc82-121">Element</span></span>|<span data-ttu-id="adc82-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adc82-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adc82-123">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="adc82-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="adc82-124">Ne tür bir ileti günlüğe denetlemek için kullanılan XPath filtreleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="adc82-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adc82-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="adc82-125">Remarks</span></span>  
 <span data-ttu-id="adc82-126">Tarafından belirtilen yalnızca Aktarım katmanında, filtrelerin uygulandığı `logMessagesAtTransportLevel` olan `true`.</span><span class="sxs-lookup"><span data-stu-id="adc82-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="adc82-127">Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğe kaydetme, filtreler tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="adc82-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="adc82-128">Koleksiyona bir filtre eklemek için kullanın `add` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="adc82-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="adc82-129">Bir veya daha fazla filtre tanımlandığında, en az bir filtre ile eşleşen iletileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="adc82-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="adc82-130">Hiçbir filtre tanımlanmış olması durumunda, tüm iletileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="adc82-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="adc82-131">Filtreler tam XPath sözdizimini desteklemek ve yapılandırma dosyasında göründükleri sırada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="adc82-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="adc82-132">Sözdizimsel olarak yanlış bir filtre yapılandırma istisnası ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="adc82-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="adc82-133">SOAP üstbilgi bölümü olan iletiler kaydeden filtreyi yapılandırmak nasıl bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="adc82-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adc82-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="adc82-134">Example</span></span>  
 <span data-ttu-id="adc82-135">SOAP üstbilgi bölümü olan iletiler kaydeden filtreyi yapılandırmak nasıl bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="adc82-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"  
     logMalformedMessages="true" logMessagesAtServiceLevel="true"  
     logMessagesAtTransportLevel="true" maxMessagesToLog="420">  
     <filters>  
        <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                        /soap:Envelope/soap:Headers  
        </add>  
     </filters>  
</messageLogging>  
```  
  
## <a name="see-also"></a><span data-ttu-id="adc82-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="adc82-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [<span data-ttu-id="adc82-137">Günlüğe İleti Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="adc82-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="adc82-138">Günlüğe İleti Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="adc82-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="adc82-139">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="adc82-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
