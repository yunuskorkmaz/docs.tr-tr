---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: a87966f643fe46d0ef69f843dc306151ca7c18bb
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400591"
---
# <a name="behaviors"></a><span data-ttu-id="60b33-101">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="60b33-101">\<behaviors></span></span>
<span data-ttu-id="60b33-102">Bu öğe, ve `endpointBehaviors` `serviceBehaviors`adlı iki alt koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60b33-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="60b33-103">Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60b33-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="60b33-104">Her davranış öğesi, benzersiz `name` özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="60b33-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="60b33-105">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="60b33-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="60b33-106">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="60b33-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
<span data-ttu-id="60b33-107">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="60b33-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="60b33-108">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="60b33-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="60b33-109">&nbsp;&nbsp;&nbsp;&nbsp; **\<davranışlar >**</span><span class="sxs-lookup"><span data-stu-id="60b33-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60b33-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60b33-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60b33-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="60b33-111">Attributes and Elements</span></span>  
 <span data-ttu-id="60b33-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60b33-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60b33-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60b33-113">Attributes</span></span>  
 <span data-ttu-id="60b33-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="60b33-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60b33-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="60b33-115">Child Elements</span></span>  
  
|<span data-ttu-id="60b33-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="60b33-116">Element</span></span>|<span data-ttu-id="60b33-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60b33-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60b33-118">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="60b33-118">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="60b33-119">Bu yapılandırma bölümü, belirli bir uç nokta için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="60b33-119">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="60b33-120">\<Servicedavranışlar ></span><span class="sxs-lookup"><span data-stu-id="60b33-120">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="60b33-121">Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="60b33-121">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60b33-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="60b33-122">Parent Elements</span></span>  
  
|<span data-ttu-id="60b33-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="60b33-123">Element</span></span>|<span data-ttu-id="60b33-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60b33-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60b33-125">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="60b33-125">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="60b33-126">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="60b33-126">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60b33-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60b33-127">Remarks</span></span>  
 <span data-ttu-id="60b33-128">Koleksiyondan belirli bir davranışı `<remove>` kaldırmak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60b33-128">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="60b33-129">Bunu yapmak için, `name` `<remove>` öğesinin özniteliğinde kaldırılacak davranışın adını sağlamanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="60b33-129">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="60b33-130">Ayrıca, `<clear>` bir davranış koleksiyonunun, koleksiyonun tüm içeriğini temizleyerek boş bir şekilde başlamasını sağlamak için öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60b33-130">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60b33-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60b33-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="60b33-132">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="60b33-132">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="60b33-133">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="60b33-133">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="60b33-134">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="60b33-134">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="60b33-135">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="60b33-135">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="60b33-136">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="60b33-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
