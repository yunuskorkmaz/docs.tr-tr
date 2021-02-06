---
description: 'Hakkında daha fazla bilgi <behavior> edinin: <serviceBehaviors>'
title: <behavior> / <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: e34254661026ad6dcb3429ad1b381cc3e6718f27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639542"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="90a2b-103">\<behavior> / \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="90a2b-103">\<behavior> of \<serviceBehaviors></span></span>

<span data-ttu-id="90a2b-104">`behavior` Öğesi içeren bir koleksiyon için bir hizmet davranışını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="90a2b-104">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="90a2b-105">Her davranış tarafından dizine kendi `name`.</span><span class="sxs-lookup"><span data-stu-id="90a2b-105">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="90a2b-106">Hizmetler, bu ad aracılığıyla her davranışa `behaviorConfiguration` , öğesinin özniteliğini kullanarak bağlanabilir [\<endpoint>](endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="90a2b-106">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="90a2b-107">Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="90a2b-107">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="90a2b-108">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-108">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="90a2b-109">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="90a2b-109">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90a2b-110">Öğesi gibi Windows Workflow etkinliklerine özgü davranış öğeleri [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) sayfasında belgelenmiştir. [ \<behavior> \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="90a2b-110">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="90a2b-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="90a2b-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90a2b-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="90a2b-112">Attributes and Elements</span></span>  

 <span data-ttu-id="90a2b-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="90a2b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90a2b-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="90a2b-114">Attributes</span></span>  
  
|<span data-ttu-id="90a2b-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="90a2b-115">Attribute</span></span>|<span data-ttu-id="90a2b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90a2b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90a2b-117">name</span><span class="sxs-lookup"><span data-stu-id="90a2b-117">name</span></span>|<span data-ttu-id="90a2b-118">Davranışın yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="90a2b-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="90a2b-119">Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="90a2b-120">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-120">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="90a2b-121">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="90a2b-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90a2b-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="90a2b-122">Child Elements</span></span>  
  
|<span data-ttu-id="90a2b-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="90a2b-123">Element</span></span>|<span data-ttu-id="90a2b-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90a2b-124">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|<span data-ttu-id="90a2b-125">DataContractSerializer için yapılandırma verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-125">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<persistenceProvider>](persistenceprovider.md)|<span data-ttu-id="90a2b-126">Kullanılacak kalıcılık sağlayıcısı uygulamasının türünü ve Kalıcılık işlemleri için kullanılacak zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-126">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[\<routing>](routing-of-servicebehavior.md)|<span data-ttu-id="90a2b-127">Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="90a2b-127">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|<span data-ttu-id="90a2b-128">, Hizmet düzeyinde bir iletim, ileti veya gönderen için geçerliliği belirleyen bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="90a2b-128">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|<span data-ttu-id="90a2b-129">Hizmet işlemlerine erişim yetkisi veren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-129">Specifies settings that authorize access to service operations.</span></span>|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="90a2b-130">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-130">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[\<serviceDebug>](servicedebug.md)|<span data-ttu-id="90a2b-131">Bir Windows Communication Foundation (WCF) hizmeti için hata ayıklama ve yardım bilgileri özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-131">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[\<serviceDiscovery>](servicediscovery.md)|<span data-ttu-id="90a2b-132">Hizmet uç noktalarının bulunabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-132">Specifies the discoverability of service endpoints.</span></span>|  
|[\<serviceMetadata>](servicemetadata.md)|<span data-ttu-id="90a2b-133">Hizmet meta verilerinin ve ilgili bilgilerin yayınlanmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-133">Specifies the publication of service metadata and associated information.</span></span>|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|<span data-ttu-id="90a2b-134">Hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-134">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[\<serviceThrottling>](servicethrottling.md)|<span data-ttu-id="90a2b-135">Bir WCF hizmetinin azaltma mekanizmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-135">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[\<serviceTimeouts>](servicetimeouts.md)|<span data-ttu-id="90a2b-136">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-136">Specifies the timeout for a service.</span></span>|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="90a2b-137">İş akışı tabanlı WCF hizmetlerini barındırmak için bir WorkflowRuntime örneğine yönelik ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="90a2b-137">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="90a2b-138">İstek iletisi başlıklarından meta veri adresi bilgilerinin alınmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="90a2b-138">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90a2b-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="90a2b-139">Parent Elements</span></span>  
  
|<span data-ttu-id="90a2b-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="90a2b-140">Element</span></span>|<span data-ttu-id="90a2b-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90a2b-141">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="90a2b-142">Hizmet davranışı öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="90a2b-142">A collection of service behavior elements.</span></span>|
