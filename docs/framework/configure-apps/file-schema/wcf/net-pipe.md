---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397722"
---
# <a name="netpipe"></a><span data-ttu-id="457a3-102">\<net. pipe ></span><span class="sxs-lookup"><span data-stu-id="457a3-102">\<net.pipe></span></span>
<span data-ttu-id="457a3-103">Named Pipe 'ın süresini yöneten ve adlandırılmış kanallar üzerinden gelen etkinleştirme isteklerini işleyen adlandırılmış kanal etkinleştirme hizmeti için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="457a3-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
<span data-ttu-id="457a3-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="457a3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="457a3-105">&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="457a3-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="457a3-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<net. pipe >**</span><span class="sxs-lookup"><span data-stu-id="457a3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="457a3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="457a3-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="457a3-108">Tür</span><span class="sxs-lookup"><span data-stu-id="457a3-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="457a3-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="457a3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="457a3-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="457a3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="457a3-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="457a3-111">Attributes</span></span>  
  
|<span data-ttu-id="457a3-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="457a3-112">Attribute</span></span>|<span data-ttu-id="457a3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="457a3-113">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="457a3-114">Paylaşım hizmeti için dinleme uç noktasındaki en fazla bekleyen eşzamanlı iş parçacığı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="457a3-114">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="457a3-115">Varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="457a3-115">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="457a3-116">Dağıtım için bekilebilecek en fazla bağlantı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="457a3-116">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="457a3-117">Varsayılan değer 100'dür.</span><span class="sxs-lookup"><span data-stu-id="457a3-117">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="457a3-118">Çerçeveleme <xref:System.TimeSpan> verilerini okumak ve alt çizgi bağlantılarından bağlantı dağıtma işlemini gerçekleştirmek için zaman aşımını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="457a3-118">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="457a3-119">Varsayılan değer "00:00:10" dır</span><span class="sxs-lookup"><span data-stu-id="457a3-119">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="457a3-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="457a3-120">Child Elements</span></span>  
  
|<span data-ttu-id="457a3-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="457a3-121">Element</span></span>|<span data-ttu-id="457a3-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="457a3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="457a3-123">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="457a3-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="457a3-124">WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek `securityIdentifier` için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="457a3-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="457a3-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="457a3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="457a3-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="457a3-126">Element</span></span>|<span data-ttu-id="457a3-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="457a3-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="457a3-128">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="457a3-128">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="457a3-129">SMSvcHost. exe dinleyici işleminin yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="457a3-129">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="457a3-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="457a3-130">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
