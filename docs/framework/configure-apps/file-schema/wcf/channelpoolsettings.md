---
title: '&lt;ChannelPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 666602bde75cd21b5b3d16bd4d5e6cf63c12d593
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554965"
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="30146-102">&lt;ChannelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="30146-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="30146-103">Özel bağlama için kanal havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="30146-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="30146-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="30146-104">\<system.serviceModel></span></span>  
<span data-ttu-id="30146-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="30146-105">\<bindings></span></span>  
<span data-ttu-id="30146-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30146-106">\<customBinding></span></span>  
<span data-ttu-id="30146-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="30146-107">\<binding></span></span>  
<span data-ttu-id="30146-108">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="30146-108">\<oneWay></span></span>  
<span data-ttu-id="30146-109">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="30146-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30146-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30146-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30146-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30146-111">Attributes and Elements</span></span>  
 <span data-ttu-id="30146-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30146-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30146-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30146-113">Attributes</span></span>  
  
|<span data-ttu-id="30146-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="30146-114">Attribute</span></span>|<span data-ttu-id="30146-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30146-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="30146-116">Bir pozitif <xref:System.TimeSpan> havuzdaki kanalların boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="30146-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="30146-117">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="30146-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="30146-118">A <xref:System.TimeSpan> sonra havuza geri döndürülen bir kanal kapalı zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="30146-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="30146-119">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="30146-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="30146-120">Her uzak uç noktası için havuzda depolanabilen kanal maksimum sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="30146-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="30146-121">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="30146-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30146-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30146-122">Child Elements</span></span>  
 <span data-ttu-id="30146-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="30146-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30146-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30146-124">Parent Elements</span></span>  
  
|<span data-ttu-id="30146-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="30146-125">Element</span></span>|<span data-ttu-id="30146-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30146-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30146-127">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="30146-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="30146-128">Paket için özel bir bağlama yönlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="30146-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30146-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30146-129">Remarks</span></span>  
 <span data-ttu-id="30146-130">Kotalar, kaynakların aşırı kullanımını önlemek için bir ilke mekanizması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30146-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="30146-131">Bunlar, kötü amaçlı veya istenmeyen hizmet reddi (DOS) saldırıları engeller.</span><span class="sxs-lookup"><span data-stu-id="30146-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="30146-132">Bu öğe, kanal kotalar özel bir kanalda ayarlarken kullanın.</span><span class="sxs-lookup"><span data-stu-id="30146-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="30146-133">`ChannelPoolSettings` üç kotaları belirtir:</span><span class="sxs-lookup"><span data-stu-id="30146-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="30146-134">`idleTimeout` Kota, sunucu üzerinde uzun bir süre için kaynakları bağlamadan üzerinde kullanan hizmet reddi (DOS) saldırıları azaltmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30146-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="30146-135">İstemcide, doğru değeri ayarı ile hizmetine güvenilirliğini artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30146-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="30146-136">Varsayılan değer, bir ölçülü uygun kaynakların ayrılması üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="30146-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="30146-137">Bu, bir geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="30146-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="30146-138">Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="30146-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="30146-139">`leaseTimeout` Kotası için kullanılan yük Dengeleyiciler ile tümleştirme ve güvenilirliği için.</span><span class="sxs-lookup"><span data-stu-id="30146-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="30146-140">Varsayılan değer, bir Klasik kaynakların ayrılması üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="30146-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="30146-141">Bu, bir geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="30146-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="30146-142">Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="30146-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="30146-143">`maxOutboundChannelsPerEndpoint` Kota önbellek sınırlarını hem sunucu hem de istemci üzerinde ayarlar ve güvenilirliğini artırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30146-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="30146-144">Varsayılan değer, bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan ölçülü uygun kaynakların ayrılması dayanır.</span><span class="sxs-lookup"><span data-stu-id="30146-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="30146-145">Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="30146-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30146-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30146-146">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="30146-147">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="30146-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [<span data-ttu-id="30146-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="30146-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="30146-149">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="30146-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="30146-150">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="30146-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="30146-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30146-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
