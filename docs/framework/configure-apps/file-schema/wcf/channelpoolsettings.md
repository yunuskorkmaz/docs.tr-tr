---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: dd81821c74678cae8602458fe796a72bf5d379e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919553"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="15de3-101">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="15de3-101">\<channelPoolSettings></span></span>
<span data-ttu-id="15de3-102">Özel bağlama için kanal havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15de3-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="15de3-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="15de3-103">\<system.serviceModel></span></span>  
<span data-ttu-id="15de3-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="15de3-104">\<bindings></span></span>  
<span data-ttu-id="15de3-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="15de3-105">\<customBinding></span></span>  
<span data-ttu-id="15de3-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="15de3-106">\<binding></span></span>  
<span data-ttu-id="15de3-107">\<tek yönlü ></span><span class="sxs-lookup"><span data-stu-id="15de3-107">\<oneWay></span></span>  
<span data-ttu-id="15de3-108">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="15de3-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15de3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15de3-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15de3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15de3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="15de3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15de3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15de3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15de3-112">Attributes</span></span>  
  
|<span data-ttu-id="15de3-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="15de3-113">Attribute</span></span>|<span data-ttu-id="15de3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15de3-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="15de3-115">Havuzdaki kanalların <xref:System.TimeSpan> kesilmeden önce boşta kalabileceği maksimum süreyi belirten bir pozitif değer.</span><span class="sxs-lookup"><span data-stu-id="15de3-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="15de3-116">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="15de3-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="15de3-117">Bir <xref:System.TimeSpan> kanalın, havuzdan döndürülmeden sonraki zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15de3-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="15de3-118">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="15de3-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="15de3-119">Her bir uzak uç nokta için havuzda depolanabilen en fazla kanal sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="15de3-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="15de3-120">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="15de3-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15de3-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15de3-121">Child Elements</span></span>  
 <span data-ttu-id="15de3-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="15de3-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15de3-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15de3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="15de3-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="15de3-124">Element</span></span>|<span data-ttu-id="15de3-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15de3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15de3-126">\<tek yönlü ></span><span class="sxs-lookup"><span data-stu-id="15de3-126">\<oneWay></span></span>](oneway.md)|<span data-ttu-id="15de3-127">Özel bağlama için paket yönlendirmeye izin vermez.</span><span class="sxs-lookup"><span data-stu-id="15de3-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15de3-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15de3-128">Remarks</span></span>  
 <span data-ttu-id="15de3-129">Kotalar, aşırı kaynak tüketimini engellemek için bir ilke mekanizması olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15de3-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="15de3-130">Kötü amaçlı ya da istenmeden hizmet reddi (DOS) saldırılarını engeller.</span><span class="sxs-lookup"><span data-stu-id="15de3-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="15de3-131">Özel bir kanalda kanal kotalarını ayarlarken bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="15de3-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="15de3-132">`ChannelPoolSettings`Üç kota belirtir:</span><span class="sxs-lookup"><span data-stu-id="15de3-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="15de3-133">`idleTimeout` Kota, kaynakları uzun bir süre için bağlama kullanan sunucuda hizmet reddi (DOS) saldırılarını azaltmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15de3-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="15de3-134">İstemcide, doğru değeri ayarlamak, hizmetle bağlantı kurma güvenilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="15de3-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="15de3-135">Varsayılan değer, kaynakların koruma altına göre ayrılmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="15de3-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="15de3-136">Geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="15de3-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="15de3-137">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="15de3-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="15de3-138">Kota `leaseTimeout` , yük dengeleyiciler ile tümleştirme için ve güvenilirliği iyileştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15de3-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="15de3-139">Varsayılan değer, kaynakların klasik bir ayırmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="15de3-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="15de3-140">Geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="15de3-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="15de3-141">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="15de3-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="15de3-142">`maxOutboundChannelsPerEndpoint` Kota, hem sunucu hem de istemci üzerindeki önbellek sınırlarını ayarlar ve güvenilirliği artırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15de3-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="15de3-143">Varsayılan değer, bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan kaynakların koruma altına dayalı bir şekilde ayrılmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="15de3-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="15de3-144">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="15de3-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15de3-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15de3-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="15de3-146">\<tek yönlü ></span><span class="sxs-lookup"><span data-stu-id="15de3-146">\<oneWay></span></span>](oneway.md)
- [<span data-ttu-id="15de3-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="15de3-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="15de3-148">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="15de3-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="15de3-149">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="15de3-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="15de3-150">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="15de3-150">\<customBinding></span></span>](custombinding.md)
