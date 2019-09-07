---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398164"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="48a60-101">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="48a60-101">\<channelPoolSettings></span></span>
<span data-ttu-id="48a60-102">Özel bağlama için kanal havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="48a60-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
<span data-ttu-id="48a60-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="48a60-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="48a60-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="48a60-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="48a60-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="48a60-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="48a60-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="48a60-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="48a60-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="48a60-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="48a60-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<tek yönlü >** ](oneway.md)</span><span class="sxs-lookup"><span data-stu-id="48a60-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)</span></span>\
<span data-ttu-id="48a60-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<channelPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="48a60-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48a60-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48a60-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48a60-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="48a60-111">Attributes and Elements</span></span>  
 <span data-ttu-id="48a60-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48a60-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48a60-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="48a60-113">Attributes</span></span>  
  
|<span data-ttu-id="48a60-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="48a60-114">Attribute</span></span>|<span data-ttu-id="48a60-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48a60-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="48a60-116">Havuzdaki kanalların <xref:System.TimeSpan> kesilmeden önce boşta kalabileceği maksimum süreyi belirten bir pozitif değer.</span><span class="sxs-lookup"><span data-stu-id="48a60-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="48a60-117">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="48a60-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="48a60-118">Bir <xref:System.TimeSpan> kanalın, havuzdan döndürülmeden sonraki zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="48a60-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="48a60-119">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="48a60-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="48a60-120">Her bir uzak uç nokta için havuzda depolanabilen en fazla kanal sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="48a60-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="48a60-121">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="48a60-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48a60-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="48a60-122">Child Elements</span></span>  
 <span data-ttu-id="48a60-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="48a60-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48a60-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="48a60-124">Parent Elements</span></span>  
  
|<span data-ttu-id="48a60-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="48a60-125">Element</span></span>|<span data-ttu-id="48a60-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48a60-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48a60-127">\<tek yönlü ></span><span class="sxs-lookup"><span data-stu-id="48a60-127">\<oneWay></span></span>](oneway.md)|<span data-ttu-id="48a60-128">Özel bağlama için paket yönlendirmeye izin vermez.</span><span class="sxs-lookup"><span data-stu-id="48a60-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48a60-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48a60-129">Remarks</span></span>  
 <span data-ttu-id="48a60-130">Kotalar, aşırı kaynak tüketimini engellemek için bir ilke mekanizması olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48a60-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="48a60-131">Kötü amaçlı ya da istenmeden hizmet reddi (DOS) saldırılarını engeller.</span><span class="sxs-lookup"><span data-stu-id="48a60-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="48a60-132">Özel bir kanalda kanal kotalarını ayarlarken bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="48a60-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="48a60-133">`ChannelPoolSettings`Üç kota belirtir:</span><span class="sxs-lookup"><span data-stu-id="48a60-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="48a60-134">`idleTimeout` Kota, kaynakları uzun bir süre için bağlama kullanan sunucuda hizmet reddi (DOS) saldırılarını azaltmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48a60-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="48a60-135">İstemcide, doğru değeri ayarlamak, hizmetle bağlantı kurma güvenilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="48a60-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="48a60-136">Varsayılan değer, kaynakların koruma altına göre ayrılmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="48a60-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="48a60-137">Geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="48a60-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="48a60-138">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="48a60-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="48a60-139">Kota `leaseTimeout` , yük dengeleyiciler ile tümleştirme için ve güvenilirliği iyileştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48a60-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="48a60-140">Varsayılan değer, kaynakların klasik bir ayırmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="48a60-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="48a60-141">Geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="48a60-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="48a60-142">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="48a60-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="48a60-143">`maxOutboundChannelsPerEndpoint` Kota, hem sunucu hem de istemci üzerindeki önbellek sınırlarını ayarlar ve güvenilirliği artırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48a60-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="48a60-144">Varsayılan değer, bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan kaynakların koruma altına dayalı bir şekilde ayrılmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="48a60-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="48a60-145">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="48a60-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a60-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48a60-146">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="48a60-147">\<tek yönlü ></span><span class="sxs-lookup"><span data-stu-id="48a60-147">\<oneWay></span></span>](oneway.md)
- [<span data-ttu-id="48a60-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="48a60-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="48a60-149">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="48a60-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="48a60-150">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="48a60-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="48a60-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="48a60-151">\<customBinding></span></span>](custombinding.md)
