---
title: '&lt;channelPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09496add0adcc11756b6aae01a0236fe590f819f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="641f2-102">&lt;channelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="641f2-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="641f2-103">Özel bağlama için kanal havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="641f2-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="641f2-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="641f2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="641f2-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="641f2-105">\<bindings></span></span>  
<span data-ttu-id="641f2-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="641f2-106">\<customBinding></span></span>  
<span data-ttu-id="641f2-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="641f2-107">\<binding></span></span>  
<span data-ttu-id="641f2-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="641f2-108">\<oneWay></span></span>  
<span data-ttu-id="641f2-109">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="641f2-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="641f2-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="641f2-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="641f2-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="641f2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="641f2-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="641f2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="641f2-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="641f2-113">Attributes</span></span>  
  
|<span data-ttu-id="641f2-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="641f2-114">Attribute</span></span>|<span data-ttu-id="641f2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="641f2-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="641f2-116">Bir pozitif <xref:System.TimeSpan> kanalları havuzunda boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="641f2-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="641f2-117">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="641f2-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="641f2-118">A <xref:System.TimeSpan> sonra havuza geri döner olduğunda bir kanal kapalı zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="641f2-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="641f2-119">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="641f2-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="641f2-120">Her uzak uç nokta için havuzunda saklanan kanalları en fazla sayısını belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="641f2-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="641f2-121">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="641f2-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="641f2-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="641f2-122">Child Elements</span></span>  
 <span data-ttu-id="641f2-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="641f2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="641f2-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="641f2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="641f2-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="641f2-125">Element</span></span>|<span data-ttu-id="641f2-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="641f2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="641f2-127">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="641f2-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="641f2-128">Paket için özel bir bağlama yönlendirmesini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="641f2-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="641f2-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="641f2-129">Remarks</span></span>  
 <span data-ttu-id="641f2-130">Kotalar aşırı kaynaklarının kullanımını engellemek için bir ilke mekanizması olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="641f2-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="641f2-131">Bunlar kötü amaçlı veya istenmeyen hizmet reddi (DOS) saldırılarını önler.</span><span class="sxs-lookup"><span data-stu-id="641f2-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="641f2-132">Bu öğe kanal kotaları özel bir kanalda ayarlarken kullanın.</span><span class="sxs-lookup"><span data-stu-id="641f2-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="641f2-133">`ChannelPoolSettings`üç kotaları belirtir:</span><span class="sxs-lookup"><span data-stu-id="641f2-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="641f2-134">`idleTimeout` Kota sunucusundaki kaynakları uzun bir süre için bağlamadan kullanan hizmet reddi (DOS) saldırıları azaltmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="641f2-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="641f2-135">İstemci üzerinde doğru değeri ayarı hizmetiyle bağlayan güvenilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="641f2-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="641f2-136">Varsayılan değer ölçülü uygun tahsis edilen kaynakların temel alır.</span><span class="sxs-lookup"><span data-stu-id="641f2-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="641f2-137">Bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan.</span><span class="sxs-lookup"><span data-stu-id="641f2-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="641f2-138">Hizmet yöneticileri, yüklemenin kaynakları tükendi çalıştırıyorsa veya ek kaynaklar kullanılabilirlik rağmen bağlantıları sınırlı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="641f2-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="641f2-139">`leaseTimeout` Kotası için kullanılan yük dengeleyici ile tümleştirme için ve güvenilirlik geliştirmek için.</span><span class="sxs-lookup"><span data-stu-id="641f2-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="641f2-140">Varsayılan değer koruyucu tahsis edilen kaynakların temel alır.</span><span class="sxs-lookup"><span data-stu-id="641f2-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="641f2-141">Bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan.</span><span class="sxs-lookup"><span data-stu-id="641f2-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="641f2-142">Hizmet yöneticileri, yüklemenin kaynakları tükendi çalıştırıyorsa veya ek kaynaklar kullanılabilirlik rağmen bağlantıları sınırlı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="641f2-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="641f2-143">`maxOutboundChannelsPerEndpoint` Kota hem sunucu hem de istemci önbellek sınırlarını ayarlar ve güvenilirliğini artırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="641f2-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="641f2-144">Varsayılan değer bir geliştirme ortamı ve küçük yükleme senaryoları için uygun bir ölçülü uygun ayırma kaynakların temel alır.</span><span class="sxs-lookup"><span data-stu-id="641f2-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="641f2-145">Hizmet yöneticileri, yüklemenin kaynakları tükendi çalıştırıyorsa veya ek kaynaklar kullanılabilirlik rağmen bağlantıları sınırlı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="641f2-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="641f2-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="641f2-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="641f2-147">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="641f2-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [<span data-ttu-id="641f2-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="641f2-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="641f2-149">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="641f2-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="641f2-150">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="641f2-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="641f2-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="641f2-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
