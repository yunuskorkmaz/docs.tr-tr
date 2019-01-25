---
title: '&lt;OneWay&gt;'
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: c909bce5b54976a215a59ca8fd9f097f574acd80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600303"
---
# <a name="ltonewaygt"></a><span data-ttu-id="80709-102">&lt;OneWay&gt;</span><span class="sxs-lookup"><span data-stu-id="80709-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="80709-103">Paket Yönlendirme ve özel bir bağlama için tek yönlü yöntemlerin kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="80709-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="80709-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="80709-104">\<system.serviceModel></span></span>  
<span data-ttu-id="80709-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="80709-105">\<bindings></span></span>  
<span data-ttu-id="80709-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="80709-106">\<customBinding></span></span>  
<span data-ttu-id="80709-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="80709-107">\<binding></span></span>  
<span data-ttu-id="80709-108">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="80709-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80709-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80709-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80709-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="80709-110">Attributes and Elements</span></span>  
 <span data-ttu-id="80709-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80709-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80709-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80709-112">Attributes</span></span>  
  
|<span data-ttu-id="80709-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="80709-113">Attribute</span></span>|<span data-ttu-id="80709-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80709-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="80709-115">Paket yönlendirmenin etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="80709-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="80709-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="80709-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="80709-117">Kabul edilebilir kanal sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="80709-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80709-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="80709-118">Child Elements</span></span>  
  
|<span data-ttu-id="80709-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="80709-119">Element</span></span>|<span data-ttu-id="80709-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80709-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80709-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="80709-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="80709-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> geçerli kanal için kanal havuzu özelliklerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="80709-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80709-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="80709-123">Parent Elements</span></span>  
  
|<span data-ttu-id="80709-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="80709-124">Element</span></span>|<span data-ttu-id="80709-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80709-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80709-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="80709-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="80709-127">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80709-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80709-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80709-128">Remarks</span></span>  
 <span data-ttu-id="80709-129">Paket yönlendirme etkinleştirmek için tek yönlü dönüştürme katman gereklidir, bu öğe sağlar.</span><span class="sxs-lookup"><span data-stu-id="80709-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="80709-130">Bir kullanıcı bu bağlama paket yönlendirilebilir yapmak için oturum durumunu algılayan veya istek-yanıt aktarım Katmanlar özel bir bağlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80709-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="80709-131">Bu öğe, daha doğal bir biçimde one-way metotları kullanıma sunmak istediğiniz durumlarda da kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="80709-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="80709-132">Daha fazla dönüştürme bileşik çift yönlü ve güvenilir Mesajlaşma gibi bu katmanı üzerinden uygulanır.</span><span class="sxs-lookup"><span data-stu-id="80709-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80709-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80709-133">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="80709-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="80709-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="80709-135">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="80709-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="80709-136">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="80709-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="80709-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="80709-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
