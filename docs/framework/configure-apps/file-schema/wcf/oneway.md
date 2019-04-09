---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: bfda2b9d7b3aa5219a3e4c344347d3b10419a7bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102420"
---
# <a name="oneway"></a><span data-ttu-id="30147-101">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="30147-101">\<oneWay></span></span>
<span data-ttu-id="30147-102">Paket Yönlendirme ve özel bir bağlama için tek yönlü yöntemlerin kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="30147-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="30147-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="30147-103">\<system.serviceModel></span></span>  
<span data-ttu-id="30147-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="30147-104">\<bindings></span></span>  
<span data-ttu-id="30147-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30147-105">\<customBinding></span></span>  
<span data-ttu-id="30147-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="30147-106">\<binding></span></span>  
<span data-ttu-id="30147-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="30147-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30147-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30147-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30147-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30147-109">Attributes and Elements</span></span>  
 <span data-ttu-id="30147-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30147-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30147-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30147-111">Attributes</span></span>  
  
|<span data-ttu-id="30147-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="30147-112">Attribute</span></span>|<span data-ttu-id="30147-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30147-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="30147-114">Paket yönlendirmenin etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="30147-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="30147-115">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="30147-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="30147-116">Kabul edilebilir kanal sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="30147-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30147-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30147-117">Child Elements</span></span>  
  
|<span data-ttu-id="30147-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="30147-118">Element</span></span>|<span data-ttu-id="30147-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30147-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30147-120">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="30147-120">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="30147-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> geçerli kanal için kanal havuzu özelliklerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="30147-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30147-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30147-122">Parent Elements</span></span>  
  
|<span data-ttu-id="30147-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="30147-123">Element</span></span>|<span data-ttu-id="30147-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30147-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30147-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="30147-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="30147-126">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="30147-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30147-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30147-127">Remarks</span></span>  
 <span data-ttu-id="30147-128">Paket yönlendirme etkinleştirmek için tek yönlü dönüştürme katman gereklidir, bu öğe sağlar.</span><span class="sxs-lookup"><span data-stu-id="30147-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="30147-129">Bir kullanıcı bu bağlama paket yönlendirilebilir yapmak için oturum durumunu algılayan veya istek-yanıt aktarım Katmanlar özel bir bağlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30147-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="30147-130">Bu öğe, daha doğal bir biçimde one-way metotları kullanıma sunmak istediğiniz durumlarda da kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="30147-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="30147-131">Daha fazla dönüştürme bileşik çift yönlü ve güvenilir Mesajlaşma gibi bu katmanı üzerinden uygulanır.</span><span class="sxs-lookup"><span data-stu-id="30147-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30147-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30147-132">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="30147-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="30147-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="30147-134">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="30147-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="30147-135">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="30147-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="30147-136">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30147-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
