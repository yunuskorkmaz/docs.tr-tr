---
title: <add> / <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 399fc4e22a9253469a5494af61dac862e33814a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128706"
---
# <a name="add-of-filters"></a><span data-ttu-id="42fd7-102">\<Ekle >, \<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="42fd7-102">\<add> of \<filters></span></span>
<span data-ttu-id="42fd7-103">Günlüğe kaydedilecek ileti türünü belirten bir XPath filtresi.</span><span class="sxs-lookup"><span data-stu-id="42fd7-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="42fd7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="42fd7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="42fd7-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="42fd7-105">\<diagnostic></span></span>  
<span data-ttu-id="42fd7-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="42fd7-106">\<messageLogging></span></span>  
<span data-ttu-id="42fd7-107">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="42fd7-107">\<filters></span></span>  
<span data-ttu-id="42fd7-108">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="42fd7-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42fd7-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42fd7-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42fd7-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="42fd7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="42fd7-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42fd7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42fd7-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="42fd7-112">Attributes</span></span>  
  
|<span data-ttu-id="42fd7-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="42fd7-113">Attribute</span></span>|<span data-ttu-id="42fd7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42fd7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42fd7-115">filtre</span><span class="sxs-lookup"><span data-stu-id="42fd7-115">filter</span></span>|<span data-ttu-id="42fd7-116">Bir XPath 1.0 ifade tarafından tanımlanan bir XML belgesi üzerinde bir sorgu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="42fd7-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="42fd7-117">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="42fd7-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42fd7-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="42fd7-118">Child Elements</span></span>  
 <span data-ttu-id="42fd7-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="42fd7-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42fd7-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="42fd7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="42fd7-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="42fd7-121">Element</span></span>|<span data-ttu-id="42fd7-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42fd7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42fd7-123">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="42fd7-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="42fd7-124">Hangi tür iletilerin günlüğe denetlemek için kullanılan XPath filtrelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="42fd7-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42fd7-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42fd7-125">Remarks</span></span>  
 <span data-ttu-id="42fd7-126">Filtreler yalnızca Aktarım katmanında, tarafından belirtilen uygulanır `logMessagesAtTransportLevel` olduğu `true`.</span><span class="sxs-lookup"><span data-stu-id="42fd7-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="42fd7-127">Hizmet düzeyi ve hatalı biçimlendirilmiş bir ileti günlüğü filtreler tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="42fd7-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="42fd7-128">Koleksiyona bir filtre eklemek için `add` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="42fd7-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="42fd7-129">Bir veya daha fazla filtre tanımlandığında, en az bir filtre ile eşleşen iletileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="42fd7-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="42fd7-130">Filtre boş tanımlıysa, tüm iletileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="42fd7-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="42fd7-131">Filtreler XPath tamamını destekler ve yapılandırma dosyasında göründükleri sırayla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="42fd7-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="42fd7-132">Sözdizimsel olarak yanlış bir filtre yapılandırma bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="42fd7-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="42fd7-133">Yalnızca bir SOAP üst bilgisi bölümü olan iletiler kaydeden filtre yapılandırmak nasıl bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="42fd7-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42fd7-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="42fd7-134">Example</span></span>  
 <span data-ttu-id="42fd7-135">Yalnızca bir SOAP üst bilgisi bölümü olan iletiler kaydeden filtre yapılandırmak nasıl bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="42fd7-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42fd7-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42fd7-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="42fd7-137">Günlüğe İleti Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="42fd7-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="42fd7-138">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="42fd7-138">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
