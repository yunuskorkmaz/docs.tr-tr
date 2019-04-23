---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 108c349a44ed3ac902652f86241c1e96a622549b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204243"
---
# <a name="behaviors"></a><span data-ttu-id="c5bc4-101">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c5bc4-101">\<behaviors></span></span>
<span data-ttu-id="c5bc4-102">Bu öğe adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="c5bc4-103">Her koleksiyon sırasıyla uç noktaları ve hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="c5bc4-104">Her davranışı öğesi kendi benzersiz tarafından tanımlanır `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="c5bc4-105">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c5bc4-106">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c5bc4-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="c5bc4-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c5bc4-107">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5bc4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5bc4-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5bc4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5bc4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c5bc4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5bc4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5bc4-111">Attributes</span></span>  
 <span data-ttu-id="c5bc4-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c5bc4-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5bc4-113">Child Elements</span></span>  
  
|<span data-ttu-id="c5bc4-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5bc4-114">Element</span></span>|<span data-ttu-id="c5bc4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5bc4-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5bc4-116">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c5bc4-116">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="c5bc4-117">Bu yapılandırma bölümü, belirli bir uç nokta için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-117">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="c5bc4-118">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c5bc4-118">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="c5bc4-119">Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-119">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5bc4-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5bc4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c5bc4-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5bc4-121">Element</span></span>|<span data-ttu-id="c5bc4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5bc4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5bc4-123">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c5bc4-123">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="c5bc4-124">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-124">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5bc4-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5bc4-125">Remarks</span></span>  
 <span data-ttu-id="c5bc4-126">Kullanabileceğiniz `<remove>` koleksiyondan belirli bir davranış öğesi.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-126">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="c5bc4-127">Bunu yapmak için basitçe kaldırmak için davranış adı sağlamanız `name` özniteliği `<remove>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-127">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="c5bc4-128">Ayrıca `<clear>` koleksiyonun tüm içeriği teslim temizleyerek bir davranış koleksiyonu boş başladığını sağlamak üzere öğesi.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-128">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5bc4-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5bc4-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="c5bc4-130">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="c5bc4-130">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="c5bc4-131">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c5bc4-131">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="c5bc4-132">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="c5bc4-132">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="c5bc4-133">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="c5bc4-133">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="c5bc4-134">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="c5bc4-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
