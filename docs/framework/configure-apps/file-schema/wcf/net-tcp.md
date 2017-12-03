---
title: '&lt;NET.TCP&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4a63d32cc4c0e48b8d3fb40526d810e2f66089d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltnettcpgt"></a><span data-ttu-id="41d5d-102">&lt;NET.TCP&gt;</span><span class="sxs-lookup"><span data-stu-id="41d5d-102">&lt;net.tcp&gt;</span></span>
<span data-ttu-id="41d5d-103">Ağ Yapılandırması ayarlarını belirtir. TCP bağlantı noktası paylaşımı aynı TCP bağlantı noktasını paylaşmak birden çok işlemlerinin sağlayan hizmet.</span><span class="sxs-lookup"><span data-stu-id="41d5d-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="41d5d-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="41d5d-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="41d5d-105">\<NET.TCP ></span><span class="sxs-lookup"><span data-stu-id="41d5d-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d5d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41d5d-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="41d5d-107">Tür</span><span class="sxs-lookup"><span data-stu-id="41d5d-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41d5d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="41d5d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="41d5d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41d5d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41d5d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="41d5d-110">Attributes</span></span>  
  
|<span data-ttu-id="41d5d-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="41d5d-111">Attribute</span></span>|<span data-ttu-id="41d5d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41d5d-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="41d5d-113">Paylaşılan bağlantı kabul edilir, ancak henüz için gönderilir değil en fazla bekleyen bağlantı belirten bir tamsayı [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="41d5d-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="41d5d-114">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="41d5d-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="41d5d-115">Dinleme bitiş Paylaşım Hizmeti için en çok bekleyen eşzamanlı kabul iş parçacığı belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="41d5d-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="41d5d-116">Varsayılan değer 2'dir.</span><span class="sxs-lookup"><span data-stu-id="41d5d-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="41d5d-117">Uygulama tarafından kabul edilmesi için bekleyen dinleyicisi olabilir bağlantılarının maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="41d5d-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="41d5d-118">Bu kota değeri aşıldığında, yeni gelen bağlantıları bırakılan yerine kabul edilmesi için bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="41d5d-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="41d5d-119">İleti güvenliği gibi bağlantı özellikleri birden fazla bağlantı açmak bir istemci neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="41d5d-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="41d5d-120">Hizmet yöneticileri bu ek bağlantılar için bu kota değeri ayarlanırken dikkate.</span><span class="sxs-lookup"><span data-stu-id="41d5d-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="41d5d-121">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="41d5d-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="41d5d-122">A `TimeSpan` çerçeveleme veri okumak ve altı çizili bağlantılarından bağlantı gönderme gerçekleştirmek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="41d5d-122">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="41d5d-123">Varsayılan değer "00: 00:10".</span><span class="sxs-lookup"><span data-stu-id="41d5d-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="41d5d-124">Hizmet bağlantı noktası TCP üzerinde dinlenecek Microsoft Teredo hizmeti kullanıp kullanmadığını belirten bir Boole değeri bağlantı noktalarını adına [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="41d5d-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="41d5d-125">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="41d5d-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41d5d-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="41d5d-126">Child Elements</span></span>  
  
|<span data-ttu-id="41d5d-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="41d5d-127">Element</span></span>|<span data-ttu-id="41d5d-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41d5d-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41d5d-129">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="41d5d-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="41d5d-130">İçeren yapılandırma öğelerinin koleksiyonu bir `securityIdentifier` kullanıcı hesapları için işlemleri barındıran belirtmek için özniteliği [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir.</span><span class="sxs-lookup"><span data-stu-id="41d5d-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41d5d-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="41d5d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="41d5d-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="41d5d-132">Element</span></span>|<span data-ttu-id="41d5d-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41d5d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41d5d-134">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="41d5d-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="41d5d-135">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="41d5d-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41d5d-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41d5d-136">Remarks</span></span>  
 <span data-ttu-id="41d5d-137">Bağlantı noktası paylaşma hakkında daha fazla bilgi için bkz: [Net.TCP bağlantı noktası paylaşma](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded).</span><span class="sxs-lookup"><span data-stu-id="41d5d-137">For more information on port sharing, see [Net.TCP Port Sharing](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded).</span></span> <span data-ttu-id="41d5d-138">Paylaşım Hizmeti bağlantı noktasını yapılandırmak nasıl anlamak için bkz: [Net.TCP bağlantı noktası Paylaşımı hizmeti yapılandırma](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span><span class="sxs-lookup"><span data-stu-id="41d5d-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d5d-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41d5d-139">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [<span data-ttu-id="41d5d-140">Net.TCP bağlantı noktası paylaşımı</span><span class="sxs-lookup"><span data-stu-id="41d5d-140">Net.TCP Port Sharing</span></span>](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="41d5d-141">Net.TCP bağlantı noktası hizmetini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="41d5d-141">Configuring the Net.TCP Port Sharing Service</span></span>](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)
