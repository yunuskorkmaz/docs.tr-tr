---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: a5c773ea91de882920775ac8dc0ecc1da68a6c9f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738796"
---
# <a name="oneway"></a><span data-ttu-id="aeff6-101">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="aeff6-101">\<oneWay></span></span>
<span data-ttu-id="aeff6-102">Paket yönlendirmeyi ve özel bağlama için tek yönlü yöntemlerin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="aeff6-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
<span data-ttu-id="aeff6-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aeff6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aeff6-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="aeff6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="aeff6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="aeff6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="aeff6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="aeff6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="aeff6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="aeff6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="aeff6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<oneWay >**</span><span class="sxs-lookup"><span data-stu-id="aeff6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeff6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aeff6-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aeff6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aeff6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aeff6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aeff6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aeff6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aeff6-112">Attributes</span></span>  
  
|<span data-ttu-id="aeff6-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aeff6-113">Attribute</span></span>|<span data-ttu-id="aeff6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeff6-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="aeff6-115">Paket yönlendirmenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="aeff6-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="aeff6-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="aeff6-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="aeff6-117">Kabul edilebilir maksimum kanal sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="aeff6-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aeff6-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aeff6-118">Child Elements</span></span>  
  
|<span data-ttu-id="aeff6-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="aeff6-119">Element</span></span>|<span data-ttu-id="aeff6-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeff6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aeff6-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="aeff6-121">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="aeff6-122">Geçerli kanal için kanal havuzunun özelliklerini içeren <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="aeff6-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aeff6-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aeff6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="aeff6-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="aeff6-124">Element</span></span>|<span data-ttu-id="aeff6-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeff6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aeff6-126">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="aeff6-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="aeff6-127">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aeff6-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeff6-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeff6-128">Remarks</span></span>  
 <span data-ttu-id="aeff6-129">Paket yönlendirmeyi etkinleştirmek için, bu öğenin sağladığı tek yönlü bir dönüştürme katmanı gerekir.</span><span class="sxs-lookup"><span data-stu-id="aeff6-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="aeff6-130">Bir Kullanıcı, bu bağlamayı bir oturum kullanan veya istek-yanıt aktarımından, BT paketini yönlendirilebilir hale getirmek için katmanlı bir özel bağlama oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="aeff6-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="aeff6-131">Bu öğe Ayrıca, tek yönlü yöntemleri daha yerel bir biçimde göstermek istediğinizde de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="aeff6-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="aeff6-132">Bu katman üzerinde bileşik çift yönlü ve güvenilir mesajlaşma gibi daha fazla dönüştürme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="aeff6-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeff6-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeff6-133">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="aeff6-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aeff6-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aeff6-135">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="aeff6-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="aeff6-136">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aeff6-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="aeff6-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="aeff6-137">\<customBinding></span></span>](custombinding.md)
