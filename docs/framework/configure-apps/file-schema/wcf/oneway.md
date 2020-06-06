---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: a5c773ea91de882920775ac8dc0ecc1da68a6c9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738796"
---
# \<oneWay>
<span data-ttu-id="39a6f-101">Paket yönlendirmeyi ve özel bağlama için tek yönlü yöntemlerin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="39a6f-101">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a><span data-ttu-id="39a6f-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39a6f-102">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39a6f-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39a6f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="39a6f-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39a6f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39a6f-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39a6f-105">Attributes</span></span>  
  
|<span data-ttu-id="39a6f-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39a6f-106">Attribute</span></span>|<span data-ttu-id="39a6f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a6f-107">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="39a6f-108">Paket yönlendirmenin etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="39a6f-108">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="39a6f-109">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="39a6f-109">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="39a6f-110">Kabul edilebilir maksimum kanal sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="39a6f-110">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39a6f-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39a6f-111">Child Elements</span></span>  
  
|<span data-ttu-id="39a6f-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="39a6f-112">Element</span></span>|<span data-ttu-id="39a6f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a6f-113">Description</span></span>|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<span data-ttu-id="39a6f-114"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>Geçerli kanal için kanal havuzunun özelliklerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="39a6f-114">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39a6f-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39a6f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="39a6f-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="39a6f-116">Element</span></span>|<span data-ttu-id="39a6f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39a6f-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="39a6f-118">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39a6f-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39a6f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39a6f-119">Remarks</span></span>  
 <span data-ttu-id="39a6f-120">Paket yönlendirmeyi etkinleştirmek için, bu öğenin sağladığı tek yönlü bir dönüştürme katmanı gerekir.</span><span class="sxs-lookup"><span data-stu-id="39a6f-120">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="39a6f-121">Bir Kullanıcı, bu bağlamayı bir oturum kullanan veya istek-yanıt aktarımından, BT paketini yönlendirilebilir hale getirmek için katmanlı bir özel bağlama oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="39a6f-121">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="39a6f-122">Bu öğe Ayrıca, tek yönlü yöntemleri daha yerel bir biçimde göstermek istediğinizde de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="39a6f-122">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="39a6f-123">Bu katman üzerinde bileşik çift yönlü ve güvenilir mesajlaşma gibi daha fazla dönüştürme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="39a6f-123">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a6f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39a6f-124">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="39a6f-125">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="39a6f-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="39a6f-126">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="39a6f-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="39a6f-127">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="39a6f-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
