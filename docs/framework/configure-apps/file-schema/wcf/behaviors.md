---
description: 'Hakkında daha fazla bilgi edinin: <behaviors>'
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 3cb8edea76f6e7af3c3b387e5b04b89e58a28305
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639516"
---
# \<behaviors>

<span data-ttu-id="e381f-102">Bu öğe, ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="e381f-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="e381f-103">Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e381f-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="e381f-104">Her davranış öğesi, benzersiz özniteliği tarafından tanımlanır `name` .</span><span class="sxs-lookup"><span data-stu-id="e381f-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="e381f-105">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e381f-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e381f-106">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="e381f-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="e381f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e381f-107">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e381f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e381f-108">Attributes and Elements</span></span>  

 <span data-ttu-id="e381f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e381f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e381f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e381f-110">Attributes</span></span>  

 <span data-ttu-id="e381f-111">Yok</span><span class="sxs-lookup"><span data-stu-id="e381f-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e381f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e381f-112">Child Elements</span></span>  
  
|<span data-ttu-id="e381f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="e381f-113">Element</span></span>|<span data-ttu-id="e381f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e381f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="e381f-115">Bu yapılandırma bölümü, belirli bir uç nokta için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e381f-115">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="e381f-116">Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e381f-116">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e381f-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e381f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e381f-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e381f-118">Element</span></span>|<span data-ttu-id="e381f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e381f-119">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="e381f-120">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="e381f-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e381f-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e381f-121">Remarks</span></span>  

 <span data-ttu-id="e381f-122">`<remove>`Koleksiyondan belirli bir davranışı kaldırmak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e381f-122">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="e381f-123">Bunu yapmak için, öğesinin özniteliğinde kaldırılacak davranışın adını sağlamanız yeterlidir `name` `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="e381f-123">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="e381f-124">Ayrıca, `<clear>` bir davranış koleksiyonunun, koleksiyonun tüm içeriğini temizleyerek boş bir şekilde başlamasını sağlamak için öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e381f-124">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e381f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e381f-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="e381f-126">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="e381f-126">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="e381f-127">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e381f-127">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="e381f-128">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="e381f-128">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="e381f-129">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="e381f-129">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="e381f-130">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="e381f-130">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
