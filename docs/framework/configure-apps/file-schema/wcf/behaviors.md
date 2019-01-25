---
title: '&lt;Davranışlar&gt;'
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: a6786efb289ee66da3f0635e1a86e23f9b7302d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528439"
---
# <a name="ltbehaviorsgt"></a><span data-ttu-id="40064-102">&lt;Davranışlar&gt;</span><span class="sxs-lookup"><span data-stu-id="40064-102">&lt;behaviors&gt;</span></span>
<span data-ttu-id="40064-103">Bu öğe adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="40064-103">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="40064-104">Her koleksiyon sırasıyla uç noktaları ve hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40064-104">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="40064-105">Her davranışı öğesi kendi benzersiz tarafından tanımlanır `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="40064-105">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="40064-106">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="40064-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="40064-107">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="40064-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="40064-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="40064-108">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40064-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40064-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40064-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40064-110">Attributes and Elements</span></span>  
 <span data-ttu-id="40064-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40064-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40064-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40064-112">Attributes</span></span>  
 <span data-ttu-id="40064-113">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="40064-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40064-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40064-114">Child Elements</span></span>  
  
|<span data-ttu-id="40064-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="40064-115">Element</span></span>|<span data-ttu-id="40064-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40064-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40064-117">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="40064-117">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="40064-118">Bu yapılandırma bölümü, belirli bir uç nokta için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="40064-118">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="40064-119">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="40064-119">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="40064-120">Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="40064-120">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40064-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40064-121">Parent Elements</span></span>  
  
|<span data-ttu-id="40064-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="40064-122">Element</span></span>|<span data-ttu-id="40064-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40064-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40064-124">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="40064-124">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="40064-125">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="40064-125">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40064-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40064-126">Remarks</span></span>  
 <span data-ttu-id="40064-127">Kullanabileceğiniz `<remove>` koleksiyondan belirli bir davranış öğesi.</span><span class="sxs-lookup"><span data-stu-id="40064-127">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="40064-128">Bunu yapmak için basitçe kaldırmak için davranış adı sağlamanız `name` özniteliği `<remove>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="40064-128">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="40064-129">Ayrıca `<clear>` koleksiyonun tüm içeriği teslim temizleyerek bir davranış koleksiyonu boş başladığını sağlamak üzere öğesi.</span><span class="sxs-lookup"><span data-stu-id="40064-129">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40064-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40064-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="40064-131">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="40064-131">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="40064-132">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="40064-132">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="40064-133">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="40064-133">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="40064-134">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="40064-134">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="40064-135">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="40064-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
