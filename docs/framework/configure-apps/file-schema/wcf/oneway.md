---
title: "&lt;tek yönlü&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 79dd5dd0ca383cebc5f08f3e12c6c6261d11a02a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltonewaygt"></a><span data-ttu-id="b9e1e-102">&lt;tek yönlü&gt;</span><span class="sxs-lookup"><span data-stu-id="b9e1e-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="b9e1e-103">Paket Yönlendirme ve özel bağlama için tek yönlü yöntemlerinin kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="b9e1e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b9e1e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b9e1e-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b9e1e-105">\<bindings></span></span>  
<span data-ttu-id="b9e1e-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b9e1e-106">\<customBinding></span></span>  
<span data-ttu-id="b9e1e-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b9e1e-107">\<binding></span></span>  
<span data-ttu-id="b9e1e-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="b9e1e-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9e1e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9e1e-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9e1e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9e1e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b9e1e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9e1e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b9e1e-112">Attributes</span></span>  
  
|<span data-ttu-id="b9e1e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b9e1e-113">Attribute</span></span>|<span data-ttu-id="b9e1e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9e1e-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="b9e1e-115">Paket yönlendirme etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="b9e1e-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="b9e1e-117">Kabul edilebilir kanal maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9e1e-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9e1e-118">Child Elements</span></span>  
  
|<span data-ttu-id="b9e1e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="b9e1e-119">Element</span></span>|<span data-ttu-id="b9e1e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9e1e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9e1e-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="b9e1e-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="b9e1e-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> geçerli kanal kanal havuzunun özelliklerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9e1e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9e1e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b9e1e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b9e1e-124">Element</span></span>|<span data-ttu-id="b9e1e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9e1e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9e1e-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b9e1e-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b9e1e-127">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9e1e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9e1e-128">Remarks</span></span>  
 <span data-ttu-id="b9e1e-129">Paket yönlendirmeyi etkinleştirmek için bir tek yönlü dönüştürme katman gereklidir, bu öğe sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="b9e1e-130">Bir kullanıcı bu bağlama paket yönlendirilebilir yapmak için bir oturum algılayan veya istek-yanıt aktarma üzerinden Katmanlar özel bir bağlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="b9e1e-131">Bu öğe, ayrıca tek yönlü yöntemleri daha yerel bir şekilde kullanıma sunmak istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="b9e1e-132">Daha fazla dönüştürmeleri bileşik çift yönlü ve güvenilir Mesajlaşma gibi bu katmanı üzerinden uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e1e-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9e1e-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="b9e1e-134">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="b9e1e-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b9e1e-135">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="b9e1e-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b9e1e-136">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b9e1e-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b9e1e-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b9e1e-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
