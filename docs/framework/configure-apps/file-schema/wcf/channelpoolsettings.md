---
title: '&lt;ChannelPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: e55d3a989ae35d6e29062337cc79114a204608bb
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149104"
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="35d69-102">&lt;ChannelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="35d69-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="35d69-103">Özel bağlama için kanal havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35d69-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="35d69-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="35d69-104">\<system.serviceModel></span></span>  
<span data-ttu-id="35d69-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="35d69-105">\<bindings></span></span>  
<span data-ttu-id="35d69-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="35d69-106">\<customBinding></span></span>  
<span data-ttu-id="35d69-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="35d69-107">\<binding></span></span>  
<span data-ttu-id="35d69-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="35d69-108">\<oneWay></span></span>  
<span data-ttu-id="35d69-109">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="35d69-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35d69-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35d69-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35d69-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="35d69-111">Attributes and Elements</span></span>  
 <span data-ttu-id="35d69-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35d69-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35d69-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="35d69-113">Attributes</span></span>  
  
|<span data-ttu-id="35d69-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="35d69-114">Attribute</span></span>|<span data-ttu-id="35d69-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35d69-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="35d69-116">Bir pozitif <xref:System.TimeSpan> havuzdaki kanalların boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="35d69-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="35d69-117">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="35d69-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="35d69-118">A <xref:System.TimeSpan> sonra havuza geri döndürülen bir kanal kapalı zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35d69-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="35d69-119">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="35d69-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="35d69-120">Her uzak uç noktası için havuzda depolanabilen kanal maksimum sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="35d69-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="35d69-121">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="35d69-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35d69-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="35d69-122">Child Elements</span></span>  
 <span data-ttu-id="35d69-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="35d69-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35d69-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="35d69-124">Parent Elements</span></span>  
  
|<span data-ttu-id="35d69-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="35d69-125">Element</span></span>|<span data-ttu-id="35d69-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35d69-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35d69-127">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="35d69-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="35d69-128">Paket için özel bir bağlama yönlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="35d69-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35d69-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35d69-129">Remarks</span></span>  
 <span data-ttu-id="35d69-130">Kotalar, kaynakların aşırı kullanımını önlemek için bir ilke mekanizması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35d69-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="35d69-131">Bunlar, kötü amaçlı veya istenmeyen hizmet reddi (DOS) saldırıları engeller.</span><span class="sxs-lookup"><span data-stu-id="35d69-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="35d69-132">Bu öğe, kanal kotalar özel bir kanalda ayarlarken kullanın.</span><span class="sxs-lookup"><span data-stu-id="35d69-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="35d69-133">`ChannelPoolSettings` üç kotaları belirtir:</span><span class="sxs-lookup"><span data-stu-id="35d69-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="35d69-134">`idleTimeout` Kota, sunucu üzerinde uzun bir süre için kaynakları bağlamadan üzerinde kullanan hizmet reddi (DOS) saldırıları azaltmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35d69-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="35d69-135">İstemcide, doğru değeri ayarı ile hizmetine güvenilirliğini artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35d69-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="35d69-136">Varsayılan değer, bir ölçülü uygun kaynakların ayrılması üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="35d69-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="35d69-137">Bu, bir geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="35d69-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="35d69-138">Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="35d69-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="35d69-139">`leaseTimeout` Kotası için kullanılan yük Dengeleyiciler ile tümleştirme ve güvenilirliği için.</span><span class="sxs-lookup"><span data-stu-id="35d69-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="35d69-140">Varsayılan değer, bir Klasik kaynakların ayrılması üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="35d69-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="35d69-141">Bu, bir geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="35d69-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="35d69-142">Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="35d69-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="35d69-143">`maxOutboundChannelsPerEndpoint` Kota önbellek sınırlarını hem sunucu hem de istemci üzerinde ayarlar ve güvenilirliğini artırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35d69-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="35d69-144">Varsayılan değer, bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan ölçülü uygun kaynakların ayrılması dayanır.</span><span class="sxs-lookup"><span data-stu-id="35d69-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="35d69-145">Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="35d69-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35d69-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35d69-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="35d69-147">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="35d69-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [<span data-ttu-id="35d69-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="35d69-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="35d69-149">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="35d69-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="35d69-150">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="35d69-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="35d69-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="35d69-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
