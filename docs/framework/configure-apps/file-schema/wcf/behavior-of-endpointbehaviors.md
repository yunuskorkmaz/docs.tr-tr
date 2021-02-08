---
description: 'Hakkında daha fazla bilgi <behavior> edinin: <endpointBehaviors>'
title: <behavior> / <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: a72bb69cce96d72cdc00d48546244bdcde20271f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802339"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="156a5-103">\<behavior> / \<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="156a5-103">\<behavior> of \<endpointBehaviors></span></span>

<span data-ttu-id="156a5-104">`behavior`Öğesi, bir uç nokta davranışı için ayarların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="156a5-104">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="156a5-105">Her davranış tarafından dizine kendi `name`.</span><span class="sxs-lookup"><span data-stu-id="156a5-105">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="156a5-106">Uç noktalar, bu ad aracılığıyla her davranışa bağlantı verebilir.</span><span class="sxs-lookup"><span data-stu-id="156a5-106">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="156a5-107">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="156a5-107">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="156a5-108">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="156a5-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="156a5-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="156a5-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="156a5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="156a5-110">Attributes and Elements</span></span>  

 <span data-ttu-id="156a5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="156a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="156a5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="156a5-112">Attributes</span></span>  
  
|<span data-ttu-id="156a5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="156a5-113">Attribute</span></span>|<span data-ttu-id="156a5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="156a5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="156a5-115">name</span><span class="sxs-lookup"><span data-stu-id="156a5-115">name</span></span>|<span data-ttu-id="156a5-116">Davranışın yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="156a5-116">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="156a5-117">Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="156a5-117">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="156a5-118">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="156a5-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="156a5-119">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="156a5-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="156a5-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="156a5-120">Child Elements</span></span>  
  
|<span data-ttu-id="156a5-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="156a5-121">Element</span></span>|<span data-ttu-id="156a5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="156a5-122">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="156a5-123">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="156a5-123">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[\<callbackDebug>](callbackdebug.md)|<span data-ttu-id="156a5-124">Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="156a5-124">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[\<callbackTimeouts>](callbacktimeouts.md)|<span data-ttu-id="156a5-125">İstemci geri çağırması için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="156a5-125">Specifies the timeout for the client callback.</span></span>|  
|[\<clientVia>](clientvia.md)|<span data-ttu-id="156a5-126">Bir iletinin gerçekleşmesi gereken yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="156a5-126">Specifies the route a message should take.</span></span>|  
|[\<dataContractSerializer>](datacontractserializer.md)|<span data-ttu-id="156a5-127">DataContractSerializer için yapılandırma verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="156a5-127">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|<span data-ttu-id="156a5-128">Bir hizmetin yanıtları zaman uyumsuz olarak göndermesini sağlayan bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="156a5-128">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[\<enableWebScript>](enablewebscript.md)|<span data-ttu-id="156a5-129">Hizmeti ASP.NET AJAX web sayfalarından tüketmek mümkün kılan uç nokta davranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="156a5-129">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="156a5-130">Davranış yalnızca \<webHttpBinding> Standart bağlama veya \<webMessageEncoding> bağlama öğesiyle birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="156a5-130">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="156a5-131">Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="156a5-131">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[\<soapProcessing>](soapprocessing.md)|<span data-ttu-id="156a5-132">Farklı bağlama türleri ve ileti sürümleri arasındaki iletileri sıralamak için kullanılan istemci uç noktası davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="156a5-132">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[\<synchronousReceive>](synchronousreceive-element.md)|<span data-ttu-id="156a5-133">Bir hizmet veya istemci uygulamasında ileti almak için çalışma zamanı davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="156a5-133">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="156a5-134">Hiçbir özniteliğe veya alt öğeye sahip değil.</span><span class="sxs-lookup"><span data-stu-id="156a5-134">It does not have any attributes or child elements.</span></span>|  
|[\<transactedBatching>](transactedbatching.md)|<span data-ttu-id="156a5-135">İşlem toplu işleminin alma işlemleri için desteklenip desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="156a5-135">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[\<webHttp>](webhttp.md)|<span data-ttu-id="156a5-136">Yapılandırma yoluyla bir uç noktada WebHttpBehavior belirtir.</span><span class="sxs-lookup"><span data-stu-id="156a5-136">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="156a5-137">Bu davranış, \<webHttpBinding> Standart bağlama birlikte kullanıldığında BIR WCF hizmeti Için Web programlama modelini sunar.</span><span class="sxs-lookup"><span data-stu-id="156a5-137">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="156a5-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="156a5-138">Parent Elements</span></span>  
  
|<span data-ttu-id="156a5-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="156a5-139">Element</span></span>|<span data-ttu-id="156a5-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="156a5-140">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="156a5-141">Uç nokta davranış öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="156a5-141">A collection of endpoint behavior elements.</span></span>|
