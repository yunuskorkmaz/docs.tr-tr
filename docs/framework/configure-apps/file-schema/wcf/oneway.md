---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f12969d8b752e54916b45c3d0e64f114971b8944
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397659"
---
# <a name="oneway"></a><span data-ttu-id="b7581-101">\<tek yönlü ></span><span class="sxs-lookup"><span data-stu-id="b7581-101">\<oneWay></span></span>
<span data-ttu-id="b7581-102">Paket yönlendirmeyi ve özel bağlama için tek yönlü yöntemlerin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="b7581-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
<span data-ttu-id="b7581-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b7581-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b7581-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b7581-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b7581-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b7581-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b7581-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b7581-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="b7581-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="b7581-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b7581-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tek yönlü >**</span><span class="sxs-lookup"><span data-stu-id="b7581-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7581-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7581-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7581-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7581-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7581-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7581-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7581-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b7581-112">Attributes</span></span>  
  
|<span data-ttu-id="b7581-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b7581-113">Attribute</span></span>|<span data-ttu-id="b7581-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7581-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="b7581-115">Paket yönlendirmenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="b7581-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="b7581-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b7581-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="b7581-117">Kabul edilebilir maksimum kanal sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b7581-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7581-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7581-118">Child Elements</span></span>  
  
|<span data-ttu-id="b7581-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="b7581-119">Element</span></span>|<span data-ttu-id="b7581-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7581-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7581-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="b7581-121">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="b7581-122">Geçerli kanal için kanal havuzunun özelliklerini içeren nesne.<xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement></span><span class="sxs-lookup"><span data-stu-id="b7581-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7581-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7581-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b7581-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b7581-124">Element</span></span>|<span data-ttu-id="b7581-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7581-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7581-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b7581-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b7581-127">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b7581-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7581-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7581-128">Remarks</span></span>  
 <span data-ttu-id="b7581-129">Paket yönlendirmeyi etkinleştirmek için, bu öğenin sağladığı tek yönlü bir dönüştürme katmanı gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7581-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="b7581-130">Bir Kullanıcı, bu bağlamayı bir oturum kullanan veya istek-yanıt aktarımından, BT paketini yönlendirilebilir hale getirmek için katmanlı bir özel bağlama oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b7581-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="b7581-131">Bu öğe Ayrıca, tek yönlü yöntemleri daha yerel bir biçimde göstermek istediğinizde de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b7581-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="b7581-132">Bu katman üzerinde bileşik çift yönlü ve güvenilir mesajlaşma gibi daha fazla dönüştürme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b7581-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7581-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7581-133">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b7581-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b7581-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b7581-135">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="b7581-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b7581-136">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b7581-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b7581-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b7581-137">\<customBinding></span></span>](custombinding.md)
