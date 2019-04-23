---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 589bae5d1f91e0424eb19cee62fe758aa7846191
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166523"
---
# <a name="nettcp"></a><span data-ttu-id="b8d39-102">\<NET.TCP ></span><span class="sxs-lookup"><span data-stu-id="b8d39-102">\<net.tcp></span></span>
<span data-ttu-id="b8d39-103">Ağ yapılandırma ayarlarını belirtir. TCP bağlantı noktası paylaşımı birden çok işlem aynı TCP bağlantı noktasını paylaşmasına izin veren hizmeti.</span><span class="sxs-lookup"><span data-stu-id="b8d39-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="b8d39-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="b8d39-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="b8d39-105">\<NET.TCP ></span><span class="sxs-lookup"><span data-stu-id="b8d39-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8d39-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8d39-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="b8d39-107">Tür</span><span class="sxs-lookup"><span data-stu-id="b8d39-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8d39-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8d39-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b8d39-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8d39-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8d39-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8d39-110">Attributes</span></span>  
  
|<span data-ttu-id="b8d39-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b8d39-111">Attribute</span></span>|<span data-ttu-id="b8d39-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8d39-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="b8d39-113">Paylaşılan bağlantıdan kabul edilir, ancak henüz Windows Communication Foundation (WCF) hizmetlerine gönderilen değil bekleyen en yüksek bağlantı belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b8d39-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="b8d39-114">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="b8d39-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="b8d39-115">Hizmetler için olan uç noktaları en fazla bekleyen eşzamanlı kabul iş parçacığı belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b8d39-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="b8d39-116">Varsayılan değer 2'dir.</span><span class="sxs-lookup"><span data-stu-id="b8d39-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="b8d39-117">Uygulama tarafından kabul edilmeyi bekliyor dinleyicinin sahip olabileceği bağlantıları sayısı.</span><span class="sxs-lookup"><span data-stu-id="b8d39-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="b8d39-118">Bu kota değeri aşıldığında, yeni gelen bağlantılar kesilir yerine kabul edilmeyi bekliyor.</span><span class="sxs-lookup"><span data-stu-id="b8d39-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="b8d39-119">Bağlantı özellikleri ileti güvenliği gibi birden fazla bağlantı açmak bir istemci neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b8d39-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="b8d39-120">Hizmet yöneticileri, bu ek bağlantılar için bu kota değeri ayarlarken hesap.</span><span class="sxs-lookup"><span data-stu-id="b8d39-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="b8d39-121">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="b8d39-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b8d39-122">A <xref:System.TimeSpan> ve çerçeveleme verilerini okumak ve altı çizili bağlantılardan bağlantı dağıtımını gerçekleştirmek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8d39-122">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="b8d39-123">Varsayılan değer "00: 00:10".</span><span class="sxs-lookup"><span data-stu-id="b8d39-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="b8d39-124">Hizmet bağlantı noktası WCF hizmetlerinin adına TCP bağlantı noktalarında dinlemek için Microsoft Teredo hizmetini kullanıp kullanmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b8d39-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="b8d39-125">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b8d39-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8d39-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8d39-126">Child Elements</span></span>  
  
|<span data-ttu-id="b8d39-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8d39-127">Element</span></span>|<span data-ttu-id="b8d39-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8d39-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8d39-129">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="b8d39-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="b8d39-130">Bir koleksiyon içeren yapılandırma öğelerinin bir `securityIdentifier` barındıran WCF hizmetleri ve Paylaşım Hizmeti bağlantı erişim izni verilen işlemleri için kullanıcı hesabı belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b8d39-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8d39-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8d39-131">Parent Elements</span></span>  
  
|<span data-ttu-id="b8d39-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8d39-132">Element</span></span>|<span data-ttu-id="b8d39-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8d39-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8d39-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="b8d39-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="b8d39-135">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b8d39-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8d39-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8d39-136">Remarks</span></span>  
 <span data-ttu-id="b8d39-137">Bağlantı noktası paylaşma ile ilgili daha fazla bilgi için bkz: [Net.TCP bağlantı noktası paylaşma](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="b8d39-137">For more information on port sharing, see [Net.TCP Port Sharing](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="b8d39-138">Bağlantı noktası hizmetini yapılandırma hakkında bilgi almak için bkz. [Net.TCP bağlantı noktası paylaşım hizmetini yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="b8d39-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d39-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8d39-139">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="b8d39-140">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="b8d39-140">Net.TCP Port Sharing</span></span>](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="b8d39-141">Net.TCP Bağlantı Noktası Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b8d39-141">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
