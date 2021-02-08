---
description: 'Hakkında daha fazla bilgi <add> edinin: <filters>'
title: <add> / <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 546ff41fddfd8a48e14508e27f09236c67c9abc9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802352"
---
# <a name="add-of-filters"></a><span data-ttu-id="1b181-103">\<add> / \<filters></span><span class="sxs-lookup"><span data-stu-id="1b181-103">\<add> of \<filters></span></span>

<span data-ttu-id="1b181-104">Günlüğe kaydedilecek ileti türünü belirten bir XPath filtresi.</span><span class="sxs-lookup"><span data-stu-id="1b181-104">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="1b181-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b181-105">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b181-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b181-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1b181-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b181-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b181-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b181-108">Attributes</span></span>  
  
|<span data-ttu-id="1b181-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1b181-109">Attribute</span></span>|<span data-ttu-id="1b181-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b181-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b181-111">filtre</span><span class="sxs-lookup"><span data-stu-id="1b181-111">filter</span></span>|<span data-ttu-id="1b181-112">Bir XPath 1,0 ifadesi tarafından tanımlanan bir XML belgesi üzerinde bir sorgu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1b181-112">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="1b181-113">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="1b181-113">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b181-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b181-114">Child Elements</span></span>  

 <span data-ttu-id="1b181-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="1b181-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b181-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b181-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1b181-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b181-117">Element</span></span>|<span data-ttu-id="1b181-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b181-118">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters.md)|<span data-ttu-id="1b181-119">Ne tür bir ileti günlüğe kaydedileceğini denetlemek için kullanılan XPath filtreleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="1b181-119">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b181-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b181-120">Remarks</span></span>  

 <span data-ttu-id="1b181-121">Filtreler yalnızca tarafından belirtilen aktarım katmanında uygulanır `logMessagesAtTransportLevel` `true` .</span><span class="sxs-lookup"><span data-stu-id="1b181-121">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="1b181-122">Hizmet düzeyi ve hatalı biçimlendirilmiş ileti günlüğe kaydetme, filtrelerle etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="1b181-122">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="1b181-123">Koleksiyona bir filtre eklemek için `add` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b181-123">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="1b181-124">Bir veya daha fazla filtre tanımlandığında yalnızca filtrelerden en az biriyle eşleşen mesajlar günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="1b181-124">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="1b181-125">Hiçbir filtre tanımlanmamışsa, tüm iletiler geçer.</span><span class="sxs-lookup"><span data-stu-id="1b181-125">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="1b181-126">Filtreler tam XPath söz dizimini destekler ve yapılandırma dosyasında göründükleri sırada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1b181-126">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="1b181-127">Sözdizimi yanlış bir filtre, yapılandırma özel durumuyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="1b181-127">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="1b181-128">Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1b181-128">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b181-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b181-129">Example</span></span>  

 <span data-ttu-id="1b181-130">Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1b181-130">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b181-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b181-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="1b181-132">İleti Günlüğe Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1b181-132">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
