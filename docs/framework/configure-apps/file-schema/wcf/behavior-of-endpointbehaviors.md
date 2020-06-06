---
title: <behavior> / <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 489678a5adeae3965acae90a847c4b087478354d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140806"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="efc78-102">\<behavior> / \<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="efc78-102">\<behavior> of \<endpointBehaviors></span></span>
<span data-ttu-id="efc78-103">`behavior`Öğesi, bir uç nokta davranışı için ayarların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="efc78-103">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="efc78-104">Her davranış tarafından dizine kendi `name`.</span><span class="sxs-lookup"><span data-stu-id="efc78-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="efc78-105">Uç noktalar, bu ad aracılığıyla her davranışa bağlantı verebilir.</span><span class="sxs-lookup"><span data-stu-id="efc78-105">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="efc78-106">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="efc78-106">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="efc78-107">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="efc78-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="efc78-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efc78-108">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efc78-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="efc78-109">Attributes and Elements</span></span>  
 <span data-ttu-id="efc78-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="efc78-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efc78-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="efc78-111">Attributes</span></span>  
  
|<span data-ttu-id="efc78-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="efc78-112">Attribute</span></span>|<span data-ttu-id="efc78-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efc78-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efc78-114">name</span><span class="sxs-lookup"><span data-stu-id="efc78-114">name</span></span>|<span data-ttu-id="efc78-115">Davranışın yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="efc78-115">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="efc78-116">Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="efc78-116">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="efc78-117">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="efc78-117">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="efc78-118">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="efc78-118">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efc78-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="efc78-119">Child Elements</span></span>  
  
|<span data-ttu-id="efc78-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="efc78-120">Element</span></span>|<span data-ttu-id="efc78-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efc78-121">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="efc78-122">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="efc78-122">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[\<callbackDebug>](callbackdebug.md)|<span data-ttu-id="efc78-123">Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="efc78-123">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[\<callbackTimeouts>](callbacktimeouts.md)|<span data-ttu-id="efc78-124">İstemci geri çağırması için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="efc78-124">Specifies the timeout for the client callback.</span></span>|  
|[\<clientVia>](clientvia.md)|<span data-ttu-id="efc78-125">Bir iletinin gerçekleşmesi gereken yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="efc78-125">Specifies the route a message should take.</span></span>|  
|[\<dataContractSerializer>](datacontractserializer.md)|<span data-ttu-id="efc78-126">DataContractSerializer için yapılandırma verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="efc78-126">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|<span data-ttu-id="efc78-127">Bir hizmetin yanıtları zaman uyumsuz olarak göndermesini sağlayan bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="efc78-127">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[\<enableWebScript>](enablewebscript.md)|<span data-ttu-id="efc78-128">Hizmeti ASP.NET AJAX web sayfalarından tüketmek mümkün kılan uç nokta davranışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="efc78-128">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="efc78-129">Davranış yalnızca \<webHttpBinding> Standart bağlama veya \<webMessageEncoding> bağlama öğesiyle birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="efc78-129">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="efc78-130">Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="efc78-130">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[\<soapProcessing>](soapprocessing.md)|<span data-ttu-id="efc78-131">Farklı bağlama türleri ve ileti sürümleri arasındaki iletileri sıralamak için kullanılan istemci uç noktası davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="efc78-131">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[\<synchronousReceive>](synchronousreceive-element.md)|<span data-ttu-id="efc78-132">Bir hizmet veya istemci uygulamasında ileti almak için çalışma zamanı davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="efc78-132">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="efc78-133">Hiçbir özniteliğe veya alt öğeye sahip değil.</span><span class="sxs-lookup"><span data-stu-id="efc78-133">It does not have any attributes or child elements.</span></span>|  
|[\<transactedBatching>](transactedbatching.md)|<span data-ttu-id="efc78-134">İşlem toplu işleminin alma işlemleri için desteklenip desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="efc78-134">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[\<webHttp>](webhttp.md)|<span data-ttu-id="efc78-135">Yapılandırma yoluyla bir uç noktada WebHttpBehavior belirtir.</span><span class="sxs-lookup"><span data-stu-id="efc78-135">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="efc78-136">Bu davranış, \<webHttpBinding> Standart bağlama birlikte kullanıldığında BIR WCF hizmeti Için Web programlama modelini sunar.</span><span class="sxs-lookup"><span data-stu-id="efc78-136">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="efc78-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="efc78-137">Parent Elements</span></span>  
  
|<span data-ttu-id="efc78-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="efc78-138">Element</span></span>|<span data-ttu-id="efc78-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efc78-139">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="efc78-140">Uç nokta davranış öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="efc78-140">A collection of endpoint behavior elements.</span></span>|
