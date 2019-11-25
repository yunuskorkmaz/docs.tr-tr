---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: bcdd26f038b343040d81b0add83bf166a5e3151f
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139693"
---
# <a name="behaviors"></a><span data-ttu-id="6396f-101">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="6396f-101">\<behaviors></span></span>
<span data-ttu-id="6396f-102">Bu öğe `endpointBehaviors` ve `serviceBehaviors`adlı iki alt koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6396f-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="6396f-103">Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6396f-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="6396f-104">Her davranış öğesi benzersiz `name` özniteliğiyle tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6396f-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="6396f-105">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6396f-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6396f-106">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="6396f-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
<span data-ttu-id="6396f-107">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6396f-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6396f-108">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6396f-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6396f-109">&nbsp;&nbsp;&nbsp;&nbsp; **\<davranışları >**</span><span class="sxs-lookup"><span data-stu-id="6396f-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6396f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6396f-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6396f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6396f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6396f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6396f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6396f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6396f-113">Attributes</span></span>  
 <span data-ttu-id="6396f-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="6396f-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6396f-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6396f-115">Child Elements</span></span>  
  
|<span data-ttu-id="6396f-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="6396f-116">Element</span></span>|<span data-ttu-id="6396f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6396f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6396f-118">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="6396f-118">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="6396f-119">Bu yapılandırma bölümü, belirli bir uç nokta için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6396f-119">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="6396f-120">\<Servicedavranışlar ></span><span class="sxs-lookup"><span data-stu-id="6396f-120">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="6396f-121">Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6396f-121">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6396f-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6396f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6396f-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="6396f-123">Element</span></span>|<span data-ttu-id="6396f-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6396f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6396f-125">\<system. serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6396f-125">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="6396f-126">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="6396f-126">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6396f-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6396f-127">Remarks</span></span>  
 <span data-ttu-id="6396f-128">Koleksiyondan belirli bir davranışı kaldırmak için `<remove>` öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6396f-128">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="6396f-129">Bunu yapmak için, `<remove>` öğesinin `name` özniteliğinde kaldırılacak davranışın adını sağlamanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="6396f-129">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="6396f-130">Ayrıca, koleksiyonun tüm içeriğini temizleyerek bir davranış koleksiyonunun boş bir şekilde başlamasını sağlamak için `<clear>` öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6396f-130">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6396f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6396f-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="6396f-132">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="6396f-132">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="6396f-133">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6396f-133">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="6396f-134">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="6396f-134">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="6396f-135">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="6396f-135">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="6396f-136">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="6396f-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
