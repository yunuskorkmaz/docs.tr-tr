---
description: 'Daha fazla bilgi edinin: <net. TCP>'
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: b7b36e0309139508011e5abceab97cc6f6f9a53d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786947"
---
# \<net.tcp>

<span data-ttu-id="014aa-103">NET için yapılandırma ayarlarını belirtir. Birden çok işlemin aynı TCP bağlantı noktasını paylaşmasına izin veren TCP bağlantı noktası paylaşım hizmeti.</span><span class="sxs-lookup"><span data-stu-id="014aa-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a><span data-ttu-id="014aa-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="014aa-104">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="014aa-105">Tür</span><span class="sxs-lookup"><span data-stu-id="014aa-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="014aa-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="014aa-106">Attributes and Elements</span></span>  

 <span data-ttu-id="014aa-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="014aa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="014aa-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="014aa-108">Attributes</span></span>  
  
|<span data-ttu-id="014aa-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="014aa-109">Attribute</span></span>|<span data-ttu-id="014aa-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="014aa-110">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="014aa-111">Paylaşılan bağlantıdan kabul edilen ancak henüz Windows Communication Foundation (WCF) hizmetlerine dağıtılan en fazla bekleyen bağlantıları belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="014aa-111">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="014aa-112">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="014aa-112">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="014aa-113">Paylaşım hizmeti için dinleme uç noktasındaki en fazla bekleyen eşzamanlı iş parçacığı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="014aa-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="014aa-114">Varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="014aa-114">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="014aa-115">Dinleyicinin uygulama tarafından kabul edilmesini bekleye, en fazla bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="014aa-115">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="014aa-116">Bu kota değeri aşıldığında, kabul edilmesini beklemek yerine yeni gelen bağlantılar bırakılır.</span><span class="sxs-lookup"><span data-stu-id="014aa-116">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="014aa-117">İleti güvenliği gibi bağlantı özellikleri istemcinin birden fazla bağlantı açmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="014aa-117">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="014aa-118">Bu kota değerini ayarlarken hizmet yöneticileri bu ek bağlantıları dikkate almalıdır.</span><span class="sxs-lookup"><span data-stu-id="014aa-118">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="014aa-119">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="014aa-119">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="014aa-120"><xref:System.TimeSpan>Çerçeveleme verilerini okumak ve alt çizgi bağlantılarından bağlantı dağıtma işlemini gerçekleştirmek için zaman aşımını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="014aa-120">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="014aa-121">Varsayılan değer "00:00:10" dır.</span><span class="sxs-lookup"><span data-stu-id="014aa-121">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="014aa-122">Bağlantı noktası paylaşım hizmetinin, WCF Hizmetleri adına TCP bağlantı noktalarında dinlemek için Microsoft Teredo hizmetini kullanıp kullanmadığını gösteren bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="014aa-122">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="014aa-123">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="014aa-123">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="014aa-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="014aa-124">Child Elements</span></span>  
  
|<span data-ttu-id="014aa-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="014aa-125">Element</span></span>|<span data-ttu-id="014aa-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="014aa-126">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="014aa-127">`securityIdentifier`WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="014aa-127">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="014aa-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="014aa-128">Parent Elements</span></span>  
  
|<span data-ttu-id="014aa-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="014aa-129">Element</span></span>|<span data-ttu-id="014aa-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="014aa-130">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="014aa-131">SMSvcHost.exe dinleyici işlemi için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="014aa-131">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="014aa-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="014aa-132">Remarks</span></span>  

 <span data-ttu-id="014aa-133">Bağlantı noktası paylaşımı hakkında daha fazla bilgi için bkz. [net. TCP bağlantı noktası paylaşma](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="014aa-133">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="014aa-134">Bağlantı noktası paylaşım hizmetini nasıl yapılandıracağınızı anlamak için bkz. [net. TCP bağlantı noktası paylaşım hizmetini yapılandırma](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="014aa-134">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014aa-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="014aa-135">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="014aa-136">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="014aa-136">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="014aa-137">Net.TCP Bağlantı Noktası Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="014aa-137">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
