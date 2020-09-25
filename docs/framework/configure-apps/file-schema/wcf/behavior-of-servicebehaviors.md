---
title: <behavior> / <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 739f95f527fd73062c8cec43efc6777efeb077f3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195161"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="c4e2d-102">\<behavior> / \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c4e2d-102">\<behavior> of \<serviceBehaviors></span></span>

<span data-ttu-id="c4e2d-103">`behavior` Öğesi içeren bir koleksiyon için bir hizmet davranışını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-103">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="c4e2d-104">Her davranış tarafından dizine kendi `name`.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="c4e2d-105">Hizmetler, bu ad aracılığıyla her davranışa `behaviorConfiguration` , öğesinin özniteliğini kullanarak bağlanabilir [\<endpoint>](endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c4e2d-105">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="c4e2d-106">Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="c4e2d-107">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-107">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c4e2d-108">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4e2d-109">Öğesi gibi Windows Workflow etkinliklerine özgü davranış öğeleri [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) sayfasında belgelenmiştir. [ \<behavior> \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c4e2d-109">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="c4e2d-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4e2d-110">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4e2d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4e2d-111">Attributes and Elements</span></span>  

 <span data-ttu-id="c4e2d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4e2d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4e2d-113">Attributes</span></span>  
  
|<span data-ttu-id="c4e2d-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c4e2d-114">Attribute</span></span>|<span data-ttu-id="c4e2d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4e2d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c4e2d-116">name</span><span class="sxs-lookup"><span data-stu-id="c4e2d-116">name</span></span>|<span data-ttu-id="c4e2d-117">Davranışın yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-117">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="c4e2d-118">Bu değer, öğe için kimlik dizesi olarak davrandığından, benzersiz olması gereken kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-118">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="c4e2d-119">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-119">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c4e2d-120">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4e2d-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4e2d-121">Child Elements</span></span>  
  
|<span data-ttu-id="c4e2d-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4e2d-122">Element</span></span>|<span data-ttu-id="c4e2d-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4e2d-123">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|<span data-ttu-id="c4e2d-124">DataContractSerializer için yapılandırma verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-124">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<persistenceProvider>](persistenceprovider.md)|<span data-ttu-id="c4e2d-125">Kullanılacak kalıcılık sağlayıcısı uygulamasının türünü ve Kalıcılık işlemleri için kullanılacak zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-125">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[\<routing>](routing-of-servicebehavior.md)|<span data-ttu-id="c4e2d-126">Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-126">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|<span data-ttu-id="c4e2d-127">, Hizmet düzeyinde bir iletim, ileti veya gönderen için geçerliliği belirleyen bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-127">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|<span data-ttu-id="c4e2d-128">Hizmet işlemlerine erişim yetkisi veren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-128">Specifies settings that authorize access to service operations.</span></span>|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="c4e2d-129">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-129">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[\<serviceDebug>](servicedebug.md)|<span data-ttu-id="c4e2d-130">Bir Windows Communication Foundation (WCF) hizmeti için hata ayıklama ve yardım bilgileri özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-130">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[\<serviceDiscovery>](servicediscovery.md)|<span data-ttu-id="c4e2d-131">Hizmet uç noktalarının bulunabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-131">Specifies the discoverability of service endpoints.</span></span>|  
|[\<serviceMetadata>](servicemetadata.md)|<span data-ttu-id="c4e2d-132">Hizmet meta verilerinin ve ilgili bilgilerin yayınlanmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-132">Specifies the publication of service metadata and associated information.</span></span>|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|<span data-ttu-id="c4e2d-133">Hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştiren ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-133">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[\<serviceThrottling>](servicethrottling.md)|<span data-ttu-id="c4e2d-134">Bir WCF hizmetinin azaltma mekanizmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-134">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[\<serviceTimeouts>](servicetimeouts.md)|<span data-ttu-id="c4e2d-135">Bir hizmet için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-135">Specifies the timeout for a service.</span></span>|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="c4e2d-136">İş akışı tabanlı WCF hizmetlerini barındırmak için bir WorkflowRuntime örneğine yönelik ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-136">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="c4e2d-137">İstek iletisi başlıklarından meta veri adresi bilgilerinin alınmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-137">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4e2d-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4e2d-138">Parent Elements</span></span>  
  
|<span data-ttu-id="c4e2d-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4e2d-139">Element</span></span>|<span data-ttu-id="c4e2d-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4e2d-140">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="c4e2d-141">Hizmet davranışı öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c4e2d-141">A collection of service behavior elements.</span></span>|
