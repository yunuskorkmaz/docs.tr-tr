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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be70abe745879b5d6f6e8cdde802a6403f90174b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltonewaygt"></a><span data-ttu-id="61d59-102">&lt;tek yönlü&gt;</span><span class="sxs-lookup"><span data-stu-id="61d59-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="61d59-103">Paket Yönlendirme ve özel bağlama için tek yönlü yöntemlerinin kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="61d59-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="61d59-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="61d59-104">\<system.serviceModel></span></span>  
<span data-ttu-id="61d59-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="61d59-105">\<bindings></span></span>  
<span data-ttu-id="61d59-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="61d59-106">\<customBinding></span></span>  
<span data-ttu-id="61d59-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="61d59-107">\<binding></span></span>  
<span data-ttu-id="61d59-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="61d59-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61d59-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61d59-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61d59-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="61d59-110">Attributes and Elements</span></span>  
 <span data-ttu-id="61d59-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="61d59-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61d59-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="61d59-112">Attributes</span></span>  
  
|<span data-ttu-id="61d59-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="61d59-113">Attribute</span></span>|<span data-ttu-id="61d59-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61d59-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="61d59-115">Paket yönlendirme etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="61d59-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="61d59-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="61d59-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="61d59-117">Kabul edilebilir kanal maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="61d59-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61d59-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="61d59-118">Child Elements</span></span>  
  
|<span data-ttu-id="61d59-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="61d59-119">Element</span></span>|<span data-ttu-id="61d59-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61d59-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61d59-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="61d59-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="61d59-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> geçerli kanal kanal havuzunun özelliklerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="61d59-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61d59-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="61d59-123">Parent Elements</span></span>  
  
|<span data-ttu-id="61d59-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="61d59-124">Element</span></span>|<span data-ttu-id="61d59-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61d59-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61d59-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="61d59-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="61d59-127">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="61d59-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61d59-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61d59-128">Remarks</span></span>  
 <span data-ttu-id="61d59-129">Paket yönlendirmeyi etkinleştirmek için bir tek yönlü dönüştürme katman gereklidir, bu öğe sağlar.</span><span class="sxs-lookup"><span data-stu-id="61d59-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="61d59-130">Bir kullanıcı bu bağlama paket yönlendirilebilir yapmak için bir oturum algılayan veya istek-yanıt aktarma üzerinden Katmanlar özel bir bağlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61d59-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="61d59-131">Bu öğe, ayrıca tek yönlü yöntemleri daha yerel bir şekilde kullanıma sunmak istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="61d59-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="61d59-132">Daha fazla dönüştürmeleri bileşik çift yönlü ve güvenilir Mesajlaşma gibi bu katmanı üzerinden uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="61d59-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61d59-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61d59-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="61d59-134">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="61d59-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="61d59-135">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="61d59-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="61d59-136">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="61d59-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="61d59-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="61d59-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
