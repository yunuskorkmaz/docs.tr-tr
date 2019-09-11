---
title: <add> / <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 280c516b17a133930bc4b6621a8c9bc7f4781085
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850556"
---
# <a name="add-of-filters"></a><span data-ttu-id="d946a-102">\<\<filtrelerin > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="d946a-102">\<add> of \<filters></span></span>
<span data-ttu-id="d946a-103">Günlüğe kaydedilecek ileti türünü belirten bir XPath filtresi.</span><span class="sxs-lookup"><span data-stu-id="d946a-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
<span data-ttu-id="d946a-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d946a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d946a-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d946a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d946a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Tanılama >** ](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="d946a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="d946a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<messageLogging >** ](messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="d946a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)</span></span>\
<span data-ttu-id="d946a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtreler >** ](filters.md)</span><span class="sxs-lookup"><span data-stu-id="d946a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)</span></span>\
<span data-ttu-id="d946a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="d946a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d946a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d946a-110">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d946a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d946a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d946a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d946a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d946a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d946a-113">Attributes</span></span>  
  
|<span data-ttu-id="d946a-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d946a-114">Attribute</span></span>|<span data-ttu-id="d946a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d946a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d946a-116">filtre</span><span class="sxs-lookup"><span data-stu-id="d946a-116">filter</span></span>|<span data-ttu-id="d946a-117">Bir XPath 1,0 ifadesi tarafından tanımlanan bir XML belgesi üzerinde bir sorgu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d946a-117">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="d946a-118">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="d946a-118">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d946a-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d946a-119">Child Elements</span></span>  
 <span data-ttu-id="d946a-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="d946a-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d946a-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d946a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d946a-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="d946a-122">Element</span></span>|<span data-ttu-id="d946a-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d946a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d946a-124">\<Filtreler ></span><span class="sxs-lookup"><span data-stu-id="d946a-124">\<filters></span></span>](filters.md)|<span data-ttu-id="d946a-125">Ne tür bir ileti günlüğe kaydedileceğini denetlemek için kullanılan XPath filtreleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d946a-125">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d946a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d946a-126">Remarks</span></span>  
 <span data-ttu-id="d946a-127">Filtreler yalnızca tarafından `logMessagesAtTransportLevel` `true`belirtilen aktarım katmanında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d946a-127">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="d946a-128">Hizmet düzeyi ve hatalı biçimlendirilmiş ileti günlüğe kaydetme, filtrelerle etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="d946a-128">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="d946a-129">Koleksiyona bir filtre eklemek için `add` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d946a-129">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="d946a-130">Bir veya daha fazla filtre tanımlandığında yalnızca filtrelerden en az biriyle eşleşen mesajlar günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="d946a-130">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="d946a-131">Hiçbir filtre tanımlanmamışsa, tüm iletiler geçer.</span><span class="sxs-lookup"><span data-stu-id="d946a-131">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="d946a-132">Filtreler tam XPath söz dizimini destekler ve yapılandırma dosyasında göründükleri sırada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d946a-132">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="d946a-133">Sözdizimi yanlış bir filtre, yapılandırma özel durumuyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="d946a-133">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="d946a-134">Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d946a-134">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d946a-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="d946a-135">Example</span></span>  
 <span data-ttu-id="d946a-136">Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d946a-136">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d946a-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d946a-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="d946a-138">Günlüğe İleti Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d946a-138">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="d946a-139">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="d946a-139">\<messageLogging></span></span>](messagelogging.md)
