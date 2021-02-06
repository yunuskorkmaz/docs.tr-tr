---
description: 'Hakkında daha fazla bilgi edinin: <channelPoolSettings>'
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 85220cac360aaf32195c0b0f1d2866729e11c442
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638983"
---
# \<channelPoolSettings>

<span data-ttu-id="ee702-102">Özel bağlama için kanal havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee702-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="ee702-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee702-103">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee702-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee702-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ee702-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee702-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee702-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee702-106">Attributes</span></span>  
  
|<span data-ttu-id="ee702-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ee702-107">Attribute</span></span>|<span data-ttu-id="ee702-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee702-108">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="ee702-109"><xref:System.TimeSpan>Havuzdaki kanalların kesilmeden önce boşta kalabileceği maksimum süreyi belirten bir pozitif değer.</span><span class="sxs-lookup"><span data-stu-id="ee702-109">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="ee702-110">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ee702-110">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="ee702-111">Bir <xref:System.TimeSpan> kanalın, havuzdan döndürülmeden sonraki zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee702-111">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="ee702-112">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ee702-112">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="ee702-113">Her bir uzak uç nokta için havuzda depolanabilen en fazla kanal sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ee702-113">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="ee702-114">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="ee702-114">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee702-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee702-115">Child Elements</span></span>  

 <span data-ttu-id="ee702-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="ee702-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee702-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee702-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ee702-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee702-118">Element</span></span>|<span data-ttu-id="ee702-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee702-119">Description</span></span>|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|<span data-ttu-id="ee702-120">Özel bağlama için paket yönlendirmeye izin vermez.</span><span class="sxs-lookup"><span data-stu-id="ee702-120">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee702-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee702-121">Remarks</span></span>  

 <span data-ttu-id="ee702-122">Kotalar, aşırı kaynak tüketimini engellemek için bir ilke mekanizması olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee702-122">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="ee702-123">Kötü amaçlı ya da istenmeden hizmet reddi (DOS) saldırılarını engeller.</span><span class="sxs-lookup"><span data-stu-id="ee702-123">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="ee702-124">Özel bir kanalda kanal kotalarını ayarlarken bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee702-124">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="ee702-125">`ChannelPoolSettings` Üç kota belirtir:</span><span class="sxs-lookup"><span data-stu-id="ee702-125">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="ee702-126">`idleTimeout`Kota, kaynakları uzun bir süre için bağlama kullanan sunucuda hizmet reddi (DOS) saldırılarını azaltmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee702-126">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="ee702-127">İstemcide, doğru değeri ayarlamak, hizmetle bağlantı kurma güvenilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="ee702-127">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="ee702-128">Varsayılan değer, kaynakların koruma altına göre ayrılmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="ee702-128">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="ee702-129">Geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="ee702-129">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="ee702-130">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="ee702-130">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="ee702-131">`leaseTimeout`Kota, yük dengeleyiciler ile tümleştirme için ve güvenilirliği iyileştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee702-131">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="ee702-132">Varsayılan değer, kaynakların klasik bir ayırmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="ee702-132">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="ee702-133">Geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="ee702-133">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="ee702-134">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="ee702-134">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="ee702-135">`maxOutboundChannelsPerEndpoint`Kota, hem sunucu hem de istemci üzerindeki önbellek sınırlarını ayarlar ve güvenilirliği artırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee702-135">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="ee702-136">Varsayılan değer, bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan kaynakların koruma altına dayalı bir şekilde ayrılmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="ee702-136">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="ee702-137">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="ee702-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee702-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee702-138">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [<span data-ttu-id="ee702-139">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ee702-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ee702-140">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="ee702-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ee702-141">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ee702-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
