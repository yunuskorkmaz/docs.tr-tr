---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 92cd6b280305c223ee125a45724691c5205ce3c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195018"
---
# \<oneWay>

<span data-ttu-id="28e21-101">Paket yönlendirmeyi ve özel bağlama için tek yönlü yöntemlerin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="28e21-101">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a><span data-ttu-id="28e21-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="28e21-102">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28e21-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="28e21-103">Attributes and Elements</span></span>  

 <span data-ttu-id="28e21-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="28e21-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28e21-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="28e21-105">Attributes</span></span>  
  
|<span data-ttu-id="28e21-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="28e21-106">Attribute</span></span>|<span data-ttu-id="28e21-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28e21-107">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="28e21-108">Paket yönlendirmenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="28e21-108">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="28e21-109">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="28e21-109">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="28e21-110">Kabul edilebilir maksimum kanal sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="28e21-110">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28e21-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="28e21-111">Child Elements</span></span>  
  
|<span data-ttu-id="28e21-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="28e21-112">Element</span></span>|<span data-ttu-id="28e21-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28e21-113">Description</span></span>|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<span data-ttu-id="28e21-114"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>Geçerli kanal için kanal havuzunun özelliklerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="28e21-114">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28e21-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="28e21-115">Parent Elements</span></span>  
  
|<span data-ttu-id="28e21-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="28e21-116">Element</span></span>|<span data-ttu-id="28e21-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28e21-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="28e21-118">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="28e21-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28e21-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28e21-119">Remarks</span></span>  

 <span data-ttu-id="28e21-120">Paket yönlendirmeyi etkinleştirmek için, bu öğenin sağladığı tek yönlü bir dönüştürme katmanı gerekir.</span><span class="sxs-lookup"><span data-stu-id="28e21-120">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="28e21-121">Bir Kullanıcı, bu bağlamayı bir oturum kullanan veya istek-yanıt aktarımından, BT paketini yönlendirilebilir hale getirmek için katmanlı bir özel bağlama oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="28e21-121">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="28e21-122">Bu öğe Ayrıca, tek yönlü yöntemleri daha yerel bir biçimde göstermek istediğinizde de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="28e21-122">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="28e21-123">Bu katman üzerinde bileşik çift yönlü ve güvenilir mesajlaşma gibi daha fazla dönüştürme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="28e21-123">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e21-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28e21-124">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="28e21-125">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="28e21-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="28e21-126">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="28e21-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="28e21-127">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="28e21-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
