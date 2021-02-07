---
description: 'Hakkında daha fazla bilgi edinin: <net. pipe>'
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: d95aebc62ab92b91c1633a99d8311b55bfaaf0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684080"
---
# \<net.pipe>

<span data-ttu-id="cf18a-103">Named Pipe 'ın süresini yöneten ve adlandırılmış kanallar üzerinden gelen etkinleştirme isteklerini işleyen adlandırılmış kanal etkinleştirme hizmeti için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf18a-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="cf18a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="cf18a-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="cf18a-105">Tür</span><span class="sxs-lookup"><span data-stu-id="cf18a-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf18a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf18a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cf18a-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf18a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf18a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cf18a-108">Attributes</span></span>  
  
|<span data-ttu-id="cf18a-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cf18a-109">Attribute</span></span>|<span data-ttu-id="cf18a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf18a-110">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="cf18a-111">Paylaşım hizmeti için dinleme uç noktasındaki en fazla bekleyen eşzamanlı iş parçacığı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cf18a-111">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="cf18a-112">Varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="cf18a-112">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="cf18a-113">Dağıtım için bekilebilecek en fazla bağlantı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cf18a-113">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="cf18a-114">Varsayılan değer 100'dür.</span><span class="sxs-lookup"><span data-stu-id="cf18a-114">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="cf18a-115"><xref:System.TimeSpan>Çerçeveleme verilerini okumak ve alt çizgi bağlantılarından bağlantı dağıtma işlemini gerçekleştirmek için zaman aşımını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="cf18a-115">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="cf18a-116">Varsayılan değer "00:00:10" dır</span><span class="sxs-lookup"><span data-stu-id="cf18a-116">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf18a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf18a-117">Child Elements</span></span>  
  
|<span data-ttu-id="cf18a-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="cf18a-118">Element</span></span>|<span data-ttu-id="cf18a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf18a-119">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="cf18a-120">`securityIdentifier`WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="cf18a-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf18a-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf18a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="cf18a-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="cf18a-122">Element</span></span>|<span data-ttu-id="cf18a-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf18a-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="cf18a-124">SMSvcHost.exe dinleyici işlemi için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cf18a-124">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf18a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf18a-125">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
