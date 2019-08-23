---
title: <add> / <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: e7975bea1435abdb77528628e7b96c65a72cbbc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926695"
---
# <a name="add-of-filters"></a><span data-ttu-id="8965f-102">\<\<filtrelerin > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="8965f-102">\<add> of \<filters></span></span>
<span data-ttu-id="8965f-103">Günlüğe kaydedilecek ileti türünü belirten bir XPath filtresi.</span><span class="sxs-lookup"><span data-stu-id="8965f-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="8965f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8965f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8965f-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="8965f-105">\<diagnostic></span></span>  
<span data-ttu-id="8965f-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="8965f-106">\<messageLogging></span></span>  
<span data-ttu-id="8965f-107">\<Filtreler ></span><span class="sxs-lookup"><span data-stu-id="8965f-107">\<filters></span></span>  
<span data-ttu-id="8965f-108">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="8965f-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8965f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8965f-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8965f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8965f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8965f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8965f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8965f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8965f-112">Attributes</span></span>  
  
|<span data-ttu-id="8965f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8965f-113">Attribute</span></span>|<span data-ttu-id="8965f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8965f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8965f-115">filtre</span><span class="sxs-lookup"><span data-stu-id="8965f-115">filter</span></span>|<span data-ttu-id="8965f-116">Bir XPath 1,0 ifadesi tarafından tanımlanan bir XML belgesi üzerinde bir sorgu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8965f-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="8965f-117">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="8965f-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8965f-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8965f-118">Child Elements</span></span>  
 <span data-ttu-id="8965f-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="8965f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8965f-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8965f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8965f-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="8965f-121">Element</span></span>|<span data-ttu-id="8965f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8965f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8965f-123">\<Filtreler ></span><span class="sxs-lookup"><span data-stu-id="8965f-123">\<filters></span></span>](filters.md)|<span data-ttu-id="8965f-124">Ne tür bir ileti günlüğe kaydedileceğini denetlemek için kullanılan XPath filtreleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8965f-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8965f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8965f-125">Remarks</span></span>  
 <span data-ttu-id="8965f-126">Filtreler yalnızca tarafından `logMessagesAtTransportLevel` `true`belirtilen aktarım katmanında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8965f-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="8965f-127">Hizmet düzeyi ve hatalı biçimlendirilmiş ileti günlüğe kaydetme, filtrelerle etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="8965f-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="8965f-128">Koleksiyona bir filtre eklemek için `add` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="8965f-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="8965f-129">Bir veya daha fazla filtre tanımlandığında yalnızca filtrelerden en az biriyle eşleşen mesajlar günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="8965f-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="8965f-130">Hiçbir filtre tanımlanmamışsa, tüm iletiler geçer.</span><span class="sxs-lookup"><span data-stu-id="8965f-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="8965f-131">Filtreler tam XPath söz dizimini destekler ve yapılandırma dosyasında göründükleri sırada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8965f-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="8965f-132">Sözdizimi yanlış bir filtre, yapılandırma özel durumuyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="8965f-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="8965f-133">Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8965f-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8965f-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="8965f-134">Example</span></span>  
 <span data-ttu-id="8965f-135">Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8965f-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8965f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8965f-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="8965f-137">Günlüğe İleti Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8965f-137">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="8965f-138">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="8965f-138">\<messageLogging></span></span>](messagelogging.md)
