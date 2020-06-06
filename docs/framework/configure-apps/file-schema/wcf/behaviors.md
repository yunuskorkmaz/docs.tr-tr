---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: bcdd26f038b343040d81b0add83bf166a5e3151f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139693"
---
# \<behaviors>
<span data-ttu-id="654e2-101">Bu öğe, ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="654e2-101">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="654e2-102">Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="654e2-102">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="654e2-103">Her davranış öğesi, benzersiz özniteliği tarafından tanımlanır `name` .</span><span class="sxs-lookup"><span data-stu-id="654e2-103">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="654e2-104">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="654e2-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="654e2-105">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="654e2-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="654e2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="654e2-106">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="654e2-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="654e2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="654e2-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="654e2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="654e2-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="654e2-109">Attributes</span></span>  
 <span data-ttu-id="654e2-110">Yok</span><span class="sxs-lookup"><span data-stu-id="654e2-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="654e2-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="654e2-111">Child Elements</span></span>  
  
|<span data-ttu-id="654e2-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="654e2-112">Element</span></span>|<span data-ttu-id="654e2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="654e2-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="654e2-114">Bu yapılandırma bölümü, belirli bir uç nokta için tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="654e2-114">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="654e2-115">Bu yapılandırma bölümü için belirli bir hizmet tanımlanan tüm davranışları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="654e2-115">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="654e2-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="654e2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="654e2-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="654e2-117">Element</span></span>|<span data-ttu-id="654e2-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="654e2-118">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="654e2-119">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="654e2-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="654e2-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="654e2-120">Remarks</span></span>  
 <span data-ttu-id="654e2-121">`<remove>`Koleksiyondan belirli bir davranışı kaldırmak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="654e2-121">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="654e2-122">Bunu yapmak için, öğesinin özniteliğinde kaldırılacak davranışın adını sağlamanız yeterlidir `name` `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="654e2-122">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="654e2-123">Ayrıca, `<clear>` bir davranış koleksiyonunun, koleksiyonun tüm içeriğini temizleyerek boş bir şekilde başlamasını sağlamak için öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="654e2-123">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654e2-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="654e2-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="654e2-125">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="654e2-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="654e2-126">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="654e2-126">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="654e2-127">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="654e2-127">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="654e2-128">Hizmet Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="654e2-128">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="654e2-129">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="654e2-129">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
