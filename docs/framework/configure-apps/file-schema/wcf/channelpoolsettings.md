---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 8638d56ccb4aaa1c5ac735aa268823af2b1fbc6d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176077"
---
# \<channelPoolSettings>

<span data-ttu-id="6b958-101">Özel bağlama için kanal havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b958-101">Specifies the channel pool settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="6b958-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b958-102">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b958-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b958-103">Attributes and Elements</span></span>  

 <span data-ttu-id="6b958-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b958-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b958-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b958-105">Attributes</span></span>  
  
|<span data-ttu-id="6b958-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6b958-106">Attribute</span></span>|<span data-ttu-id="6b958-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b958-107">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="6b958-108"><xref:System.TimeSpan>Havuzdaki kanalların kesilmeden önce boşta kalabileceği maksimum süreyi belirten bir pozitif değer.</span><span class="sxs-lookup"><span data-stu-id="6b958-108">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="6b958-109">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6b958-109">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="6b958-110">Bir <xref:System.TimeSpan> kanalın, havuzdan döndürülmeden sonraki zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b958-110">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="6b958-111">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6b958-111">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="6b958-112">Her bir uzak uç nokta için havuzda depolanabilen en fazla kanal sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6b958-112">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="6b958-113">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="6b958-113">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b958-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b958-114">Child Elements</span></span>  

 <span data-ttu-id="6b958-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="6b958-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b958-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b958-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6b958-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b958-117">Element</span></span>|<span data-ttu-id="6b958-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b958-118">Description</span></span>|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|<span data-ttu-id="6b958-119">Özel bağlama için paket yönlendirmeye izin vermez.</span><span class="sxs-lookup"><span data-stu-id="6b958-119">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b958-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b958-120">Remarks</span></span>  

 <span data-ttu-id="6b958-121">Kotalar, aşırı kaynak tüketimini engellemek için bir ilke mekanizması olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b958-121">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="6b958-122">Kötü amaçlı ya da istenmeden hizmet reddi (DOS) saldırılarını engeller.</span><span class="sxs-lookup"><span data-stu-id="6b958-122">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="6b958-123">Özel bir kanalda kanal kotalarını ayarlarken bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="6b958-123">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="6b958-124">`ChannelPoolSettings` Üç kota belirtir:</span><span class="sxs-lookup"><span data-stu-id="6b958-124">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="6b958-125">`idleTimeout`Kota, kaynakları uzun bir süre için bağlama kullanan sunucuda hizmet reddi (DOS) saldırılarını azaltmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b958-125">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="6b958-126">İstemcide, doğru değeri ayarlamak, hizmetle bağlantı kurma güvenilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="6b958-126">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="6b958-127">Varsayılan değer, kaynakların koruma altına göre ayrılmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="6b958-127">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="6b958-128">Geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="6b958-128">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="6b958-129">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="6b958-129">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="6b958-130">`leaseTimeout`Kota, yük dengeleyiciler ile tümleştirme için ve güvenilirliği iyileştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b958-130">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="6b958-131">Varsayılan değer, kaynakların klasik bir ayırmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="6b958-131">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="6b958-132">Geliştirme ortamı ve küçük yükleme senaryoları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="6b958-132">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="6b958-133">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="6b958-133">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="6b958-134">`maxOutboundChannelsPerEndpoint`Kota, hem sunucu hem de istemci üzerindeki önbellek sınırlarını ayarlar ve güvenilirliği artırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b958-134">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="6b958-135">Varsayılan değer, bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan kaynakların koruma altına dayalı bir şekilde ayrılmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="6b958-135">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="6b958-136">Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="6b958-136">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b958-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b958-137">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [<span data-ttu-id="6b958-138">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6b958-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6b958-139">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="6b958-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6b958-140">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6b958-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
