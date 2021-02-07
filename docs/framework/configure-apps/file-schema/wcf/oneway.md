---
description: 'Hakkında daha fazla bilgi edinin: <oneWay>'
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 8e3314dd14525b5f7585a7336c00b615da56d1c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683846"
---
# \<oneWay>

<span data-ttu-id="ae2ac-102">Paket yönlendirmeyi ve özel bağlama için tek yönlü yöntemlerin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a><span data-ttu-id="ae2ac-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ae2ac-103">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae2ac-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae2ac-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ae2ac-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae2ac-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ae2ac-106">Attributes</span></span>  
  
|<span data-ttu-id="ae2ac-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ae2ac-107">Attribute</span></span>|<span data-ttu-id="ae2ac-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae2ac-108">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="ae2ac-109">Paket yönlendirmenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-109">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="ae2ac-110">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-110">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="ae2ac-111">Kabul edilebilir maksimum kanal sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-111">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae2ac-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae2ac-112">Child Elements</span></span>  
  
|<span data-ttu-id="ae2ac-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae2ac-113">Element</span></span>|<span data-ttu-id="ae2ac-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae2ac-114">Description</span></span>|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<span data-ttu-id="ae2ac-115"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>Geçerli kanal için kanal havuzunun özelliklerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-115">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae2ac-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae2ac-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ae2ac-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae2ac-117">Element</span></span>|<span data-ttu-id="ae2ac-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae2ac-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="ae2ac-119">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae2ac-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae2ac-120">Remarks</span></span>  

 <span data-ttu-id="ae2ac-121">Paket yönlendirmeyi etkinleştirmek için, bu öğenin sağladığı tek yönlü bir dönüştürme katmanı gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-121">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="ae2ac-122">Bir Kullanıcı, bu bağlamayı bir oturum kullanan veya istek-yanıt aktarımından, BT paketini yönlendirilebilir hale getirmek için katmanlı bir özel bağlama oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-122">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="ae2ac-123">Bu öğe Ayrıca, tek yönlü yöntemleri daha yerel bir biçimde göstermek istediğinizde de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-123">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="ae2ac-124">Bu katman üzerinde bileşik çift yönlü ve güvenilir mesajlaşma gibi daha fazla dönüştürme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-124">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2ac-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae2ac-125">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ae2ac-126">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ae2ac-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ae2ac-127">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="ae2ac-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ae2ac-128">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ae2ac-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
