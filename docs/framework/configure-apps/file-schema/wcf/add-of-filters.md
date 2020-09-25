---
title: <add> / <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: c1de0605bc8afc502a85d9b2917b975ee45a3d26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201661"
---
# <a name="add-of-filters"></a><span data-ttu-id="a49b5-102">\<add> / \<filters></span><span class="sxs-lookup"><span data-stu-id="a49b5-102">\<add> of \<filters></span></span>

<span data-ttu-id="a49b5-103">Günlüğe kaydedilecek ileti türünü belirten bir XPath filtresi.</span><span class="sxs-lookup"><span data-stu-id="a49b5-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="a49b5-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a49b5-104">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a49b5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a49b5-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a49b5-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a49b5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a49b5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a49b5-107">Attributes</span></span>  
  
|<span data-ttu-id="a49b5-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a49b5-108">Attribute</span></span>|<span data-ttu-id="a49b5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a49b5-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a49b5-110">filtre</span><span class="sxs-lookup"><span data-stu-id="a49b5-110">filter</span></span>|<span data-ttu-id="a49b5-111">Bir XPath 1,0 ifadesi tarafından tanımlanan bir XML belgesi üzerinde bir sorgu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a49b5-111">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="a49b5-112">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="a49b5-112">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a49b5-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a49b5-113">Child Elements</span></span>  

 <span data-ttu-id="a49b5-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="a49b5-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a49b5-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a49b5-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a49b5-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="a49b5-116">Element</span></span>|<span data-ttu-id="a49b5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a49b5-117">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters.md)|<span data-ttu-id="a49b5-118">Ne tür bir ileti günlüğe kaydedileceğini denetlemek için kullanılan XPath filtreleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="a49b5-118">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a49b5-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a49b5-119">Remarks</span></span>  

 <span data-ttu-id="a49b5-120">Filtreler yalnızca tarafından belirtilen aktarım katmanında uygulanır `logMessagesAtTransportLevel` `true` .</span><span class="sxs-lookup"><span data-stu-id="a49b5-120">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="a49b5-121">Hizmet düzeyi ve hatalı biçimlendirilmiş ileti günlüğe kaydetme, filtrelerle etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="a49b5-121">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="a49b5-122">Koleksiyona bir filtre eklemek için `add` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="a49b5-122">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="a49b5-123">Bir veya daha fazla filtre tanımlandığında yalnızca filtrelerden en az biriyle eşleşen mesajlar günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a49b5-123">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="a49b5-124">Hiçbir filtre tanımlanmamışsa, tüm iletiler geçer.</span><span class="sxs-lookup"><span data-stu-id="a49b5-124">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="a49b5-125">Filtreler tam XPath söz dizimini destekler ve yapılandırma dosyasında göründükleri sırada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a49b5-125">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="a49b5-126">Sözdizimi yanlış bir filtre, yapılandırma özel durumuyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="a49b5-126">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="a49b5-127">Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a49b5-127">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a49b5-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="a49b5-128">Example</span></span>  

 <span data-ttu-id="a49b5-129">Aşağıda, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a49b5-129">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a49b5-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a49b5-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="a49b5-131">İleti Günlüğe Kaydetmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a49b5-131">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
