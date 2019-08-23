---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f4a9422f4385e37a61ec85d680fcf7743a57bc0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932939"
---
# <a name="oneway"></a><span data-ttu-id="1148d-101">\<tek yönlü ></span><span class="sxs-lookup"><span data-stu-id="1148d-101">\<oneWay></span></span>
<span data-ttu-id="1148d-102">Paket yönlendirmeyi ve özel bağlama için tek yönlü yöntemlerin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="1148d-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="1148d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1148d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="1148d-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1148d-104">\<bindings></span></span>  
<span data-ttu-id="1148d-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1148d-105">\<customBinding></span></span>  
<span data-ttu-id="1148d-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1148d-106">\<binding></span></span>  
<span data-ttu-id="1148d-107">\<tek yönlü ></span><span class="sxs-lookup"><span data-stu-id="1148d-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1148d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1148d-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1148d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1148d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1148d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1148d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1148d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1148d-111">Attributes</span></span>  
  
|<span data-ttu-id="1148d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1148d-112">Attribute</span></span>|<span data-ttu-id="1148d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1148d-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="1148d-114">Paket yönlendirmenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="1148d-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="1148d-115">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="1148d-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="1148d-116">Kabul edilebilir maksimum kanal sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="1148d-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1148d-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1148d-117">Child Elements</span></span>  
  
|<span data-ttu-id="1148d-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="1148d-118">Element</span></span>|<span data-ttu-id="1148d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1148d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1148d-120">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="1148d-120">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="1148d-121">Geçerli kanal için kanal havuzunun özelliklerini içeren nesne.<xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement></span><span class="sxs-lookup"><span data-stu-id="1148d-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1148d-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1148d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1148d-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="1148d-123">Element</span></span>|<span data-ttu-id="1148d-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1148d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1148d-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1148d-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="1148d-126">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1148d-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1148d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1148d-127">Remarks</span></span>  
 <span data-ttu-id="1148d-128">Paket yönlendirmeyi etkinleştirmek için, bu öğenin sağladığı tek yönlü bir dönüştürme katmanı gerekir.</span><span class="sxs-lookup"><span data-stu-id="1148d-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="1148d-129">Bir Kullanıcı, bu bağlamayı bir oturum kullanan veya istek-yanıt aktarımından, BT paketini yönlendirilebilir hale getirmek için katmanlı bir özel bağlama oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="1148d-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="1148d-130">Bu öğe Ayrıca, tek yönlü yöntemleri daha yerel bir biçimde göstermek istediğinizde de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1148d-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="1148d-131">Bu katman üzerinde bileşik çift yönlü ve güvenilir mesajlaşma gibi daha fazla dönüştürme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1148d-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1148d-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1148d-132">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1148d-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1148d-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1148d-134">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="1148d-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1148d-135">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1148d-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1148d-136">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1148d-136">\<customBinding></span></span>](custombinding.md)
