---
title: '&lt;Davranışları&gt;'
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: ca9cf5daa6590c14d4b5fd15c502d67af1f93b52
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbehaviorsgt"></a><span data-ttu-id="b335d-102">&lt;Davranışları&gt;</span><span class="sxs-lookup"><span data-stu-id="b335d-102">&lt;behaviors&gt;</span></span>
<span data-ttu-id="b335d-103">Bu öğe adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="b335d-103">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="b335d-104">Her koleksiyon sırasıyla uç noktaları ve hizmetler tarafından tüketilen davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b335d-104">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="b335d-105">Her davranış öğesi kendi benzersiz tanımlanır `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b335d-105">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="b335d-106">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b335d-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b335d-107">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b335d-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="b335d-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b335d-108">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b335d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b335d-109">Syntax</span></span>  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
   <endpointBehaviors>  
   </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b335d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b335d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b335d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b335d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b335d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b335d-112">Attributes</span></span>  
 <span data-ttu-id="b335d-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="b335d-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b335d-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b335d-114">Child Elements</span></span>  
  
|<span data-ttu-id="b335d-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="b335d-115">Element</span></span>|<span data-ttu-id="b335d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b335d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b335d-117">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b335d-117">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="b335d-118">Bu yapılandırma bölümü belirli bir uç noktası için tanımlanmış tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b335d-118">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="b335d-119">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b335d-119">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="b335d-120">Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b335d-120">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b335d-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b335d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b335d-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="b335d-122">Element</span></span>|<span data-ttu-id="b335d-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b335d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b335d-124">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b335d-124">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="b335d-125">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="b335d-125">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b335d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b335d-126">Remarks</span></span>  
 <span data-ttu-id="b335d-127">Kullanabileceğiniz `<remove>` belirli bir davranışı Koleksiyondan kaldırılacak öğe.</span><span class="sxs-lookup"><span data-stu-id="b335d-127">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="b335d-128">Bunu yapmak için yalnızca kaldırmak için davranış adını sağlayın `name` özniteliği `<remove>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="b335d-128">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="b335d-129">Aynı zamanda `<clear>` öğe koleksiyonunun tüm içeriği temizleyerek bir davranış koleksiyonu boş başladığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="b335d-129">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b335d-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b335d-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="b335d-131">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="b335d-131">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 [<span data-ttu-id="b335d-132">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b335d-132">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="b335d-133">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="b335d-133">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="b335d-134">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="b335d-134">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)  
 [<span data-ttu-id="b335d-135">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="b335d-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
