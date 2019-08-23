---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 63cef2b85aa57b5c1c0e0add1794ebedc73d96c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933045"
---
# <a name="nettcp"></a><span data-ttu-id="ceb6c-102">\<net. TCP ></span><span class="sxs-lookup"><span data-stu-id="ceb6c-102">\<net.tcp></span></span>
<span data-ttu-id="ceb6c-103">NET için yapılandırma ayarlarını belirtir. Birden çok işlemin aynı TCP bağlantı noktasını paylaşmasına izin veren TCP bağlantı noktası paylaşım hizmeti.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="ceb6c-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ceb6c-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="ceb6c-105">\<net. TCP ></span><span class="sxs-lookup"><span data-stu-id="ceb6c-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb6c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ceb6c-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="ceb6c-107">Tür</span><span class="sxs-lookup"><span data-stu-id="ceb6c-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceb6c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceb6c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ceb6c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceb6c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ceb6c-110">Attributes</span></span>  
  
|<span data-ttu-id="ceb6c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ceb6c-111">Attribute</span></span>|<span data-ttu-id="ceb6c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceb6c-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="ceb6c-113">Paylaşılan bağlantıdan kabul edilen ancak henüz Windows Communication Foundation (WCF) hizmetlerine dağıtılan en fazla bekleyen bağlantıları belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="ceb6c-114">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="ceb6c-115">Paylaşım hizmeti için dinleme uç noktasındaki en fazla bekleyen eşzamanlı iş parçacığı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="ceb6c-116">Varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="ceb6c-117">Dinleyicinin uygulama tarafından kabul edilmesini bekleye, en fazla bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="ceb6c-118">Bu kota değeri aşıldığında, kabul edilmesini beklemek yerine yeni gelen bağlantılar bırakılır.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="ceb6c-119">İleti güvenliği gibi bağlantı özellikleri istemcinin birden fazla bağlantı açmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="ceb6c-120">Bu kota değerini ayarlarken hizmet yöneticileri bu ek bağlantıları dikkate almalıdır.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="ceb6c-121">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ceb6c-122">Çerçeveleme <xref:System.TimeSpan> verilerini okumak ve alt çizgi bağlantılarından bağlantı dağıtma işlemini gerçekleştirmek için zaman aşımını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-122">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="ceb6c-123">Varsayılan değer "00:00:10" dır.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="ceb6c-124">Bağlantı noktası paylaşım hizmetinin, WCF Hizmetleri adına TCP bağlantı noktalarında dinlemek için Microsoft Teredo hizmetini kullanıp kullanmadığını gösteren bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="ceb6c-125">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ceb6c-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceb6c-126">Child Elements</span></span>  
  
|<span data-ttu-id="ceb6c-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="ceb6c-127">Element</span></span>|<span data-ttu-id="ceb6c-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceb6c-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceb6c-129">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="ceb6c-129">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="ceb6c-130">WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek `securityIdentifier` için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ceb6c-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ceb6c-131">Parent Elements</span></span>  
  
|<span data-ttu-id="ceb6c-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="ceb6c-132">Element</span></span>|<span data-ttu-id="ceb6c-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceb6c-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceb6c-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ceb6c-134">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="ceb6c-135">SMSvcHost. exe dinleyici işleminin yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceb6c-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ceb6c-136">Remarks</span></span>  
 <span data-ttu-id="ceb6c-137">Bağlantı noktası paylaşımı hakkında daha fazla bilgi için bkz. [net. TCP bağlantı noktası paylaşma](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="ceb6c-137">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="ceb6c-138">Bağlantı noktası paylaşım hizmetini nasıl yapılandıracağınızı anlamak için bkz. [net. TCP bağlantı noktası paylaşım hizmetini yapılandırma](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="ceb6c-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb6c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ceb6c-139">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="ceb6c-140">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="ceb6c-140">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="ceb6c-141">Net.TCP Bağlantı Noktası Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ceb6c-141">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
