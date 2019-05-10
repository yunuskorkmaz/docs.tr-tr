---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 2ad1cba170a7ade06de4678651a8dfcb608d5c46
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607208"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="5d181-101">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="5d181-101">\<channelPoolSettings></span></span>
<span data-ttu-id="5d181-102">Özel bağlama için kanal havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d181-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="5d181-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5d181-103">\<system.serviceModel></span></span>  
<span data-ttu-id="5d181-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="5d181-104">\<bindings></span></span>  
<span data-ttu-id="5d181-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5d181-105">\<customBinding></span></span>  
<span data-ttu-id="5d181-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5d181-106">\<binding></span></span>  
<span data-ttu-id="5d181-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="5d181-107">\<oneWay></span></span>  
<span data-ttu-id="5d181-108">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="5d181-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d181-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d181-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d181-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d181-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5d181-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5d181-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d181-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5d181-112">Attributes</span></span>  
  
|<span data-ttu-id="5d181-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5d181-113">Attribute</span></span>|<span data-ttu-id="5d181-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d181-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="5d181-115">Bir pozitif <xref:System.TimeSpan> havuzdaki kanalların boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d181-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="5d181-116">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5d181-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="5d181-117">A <xref:System.TimeSpan> sonra havuza geri döndürülen bir kanal kapalı zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d181-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="5d181-118">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5d181-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="5d181-119">Her uzak uç noktası için havuzda depolanabilen kanal maksimum sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5d181-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="5d181-120">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="5d181-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d181-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d181-121">Child Elements</span></span>  
 <span data-ttu-id="5d181-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d181-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d181-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d181-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5d181-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="5d181-124">Element</span></span>|<span data-ttu-id="5d181-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d181-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d181-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="5d181-126">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="5d181-127">Paket için özel bir bağlama yönlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d181-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d181-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d181-128">Remarks</span></span>  
 <span data-ttu-id="5d181-129">Kotalar, kaynakların aşırı kullanımını önlemek için bir ilke mekanizması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d181-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="5d181-130">Bunlar, kötü amaçlı veya istenmeyen hizmet reddi (DOS) saldırıları engeller.</span><span class="sxs-lookup"><span data-stu-id="5d181-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="5d181-131">Bu öğe, kanal kotalar özel bir kanalda ayarlarken kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d181-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="5d181-132">`ChannelPoolSettings` üç kotaları belirtir:</span><span class="sxs-lookup"><span data-stu-id="5d181-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="5d181-133">`idleTimeout` Kota, sunucu üzerinde uzun bir süre için kaynakları bağlamadan üzerinde kullanan hizmet reddi (DOS) saldırıları azaltmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d181-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="5d181-134">İstemcide, doğru değeri ayarı ile hizmetine güvenilirliğini artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d181-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="5d181-135">Varsayılan değer, bir ölçülü uygun kaynakların ayrılması üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="5d181-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="5d181-136">Bu, bir geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="5d181-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="5d181-137">Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="5d181-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="5d181-138">`leaseTimeout` Kotası için kullanılan yük Dengeleyiciler ile tümleştirme ve güvenilirliği için.</span><span class="sxs-lookup"><span data-stu-id="5d181-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="5d181-139">Varsayılan değer, bir Klasik kaynakların ayrılması üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="5d181-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="5d181-140">Bu, bir geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="5d181-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="5d181-141">Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="5d181-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="5d181-142">`maxOutboundChannelsPerEndpoint` Kota önbellek sınırlarını hem sunucu hem de istemci üzerinde ayarlar ve güvenilirliğini artırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d181-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="5d181-143">Varsayılan değer, bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan ölçülü uygun kaynakların ayrılması dayanır.</span><span class="sxs-lookup"><span data-stu-id="5d181-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="5d181-144">Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="5d181-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d181-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d181-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5d181-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="5d181-146">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [<span data-ttu-id="5d181-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5d181-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="5d181-148">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="5d181-148">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5d181-149">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5d181-149">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5d181-150">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5d181-150">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
