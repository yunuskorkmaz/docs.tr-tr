---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: d070b822cefeef3c281d5b0e47411f4c624dd83f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204612"
---
# \<net.pipe>

<span data-ttu-id="9d903-102">Named Pipe 'ın süresini yöneten ve adlandırılmış kanallar üzerinden gelen etkinleştirme isteklerini işleyen adlandırılmış kanal etkinleştirme hizmeti için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d903-102">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="9d903-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="9d903-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="9d903-104">Tür</span><span class="sxs-lookup"><span data-stu-id="9d903-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d903-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d903-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9d903-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d903-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d903-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9d903-107">Attributes</span></span>  
  
|<span data-ttu-id="9d903-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9d903-108">Attribute</span></span>|<span data-ttu-id="9d903-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d903-109">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="9d903-110">Paylaşım hizmeti için dinleme uç noktasındaki en fazla bekleyen eşzamanlı iş parçacığı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9d903-110">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="9d903-111">Varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="9d903-111">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="9d903-112">Dağıtım için bekilebilecek en fazla bağlantı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9d903-112">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="9d903-113">Varsayılan değer 100'dür.</span><span class="sxs-lookup"><span data-stu-id="9d903-113">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="9d903-114"><xref:System.TimeSpan>Çerçeveleme verilerini okumak ve alt çizgi bağlantılarından bağlantı dağıtma işlemini gerçekleştirmek için zaman aşımını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="9d903-114">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="9d903-115">Varsayılan değer "00:00:10" dır</span><span class="sxs-lookup"><span data-stu-id="9d903-115">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d903-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d903-116">Child Elements</span></span>  
  
|<span data-ttu-id="9d903-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="9d903-117">Element</span></span>|<span data-ttu-id="9d903-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d903-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="9d903-119">`securityIdentifier`WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="9d903-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d903-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d903-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9d903-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="9d903-121">Element</span></span>|<span data-ttu-id="9d903-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d903-122">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="9d903-123">SMSvcHost.exe dinleyici işlemi için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9d903-123">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d903-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d903-124">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
