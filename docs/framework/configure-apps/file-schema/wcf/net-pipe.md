---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 7d868d84318db8c9fe188293154dc275060a3952
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933176"
---
# <a name="netpipe"></a><span data-ttu-id="f9f93-102">\<net. pipe ></span><span class="sxs-lookup"><span data-stu-id="f9f93-102">\<net.pipe></span></span>
<span data-ttu-id="f9f93-103">Named Pipe 'ın süresini yöneten ve adlandırılmış kanallar üzerinden gelen etkinleştirme isteklerini işleyen adlandırılmış kanal etkinleştirme hizmeti için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9f93-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="f9f93-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="f9f93-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="f9f93-105">\<net. pipe ></span><span class="sxs-lookup"><span data-stu-id="f9f93-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9f93-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9f93-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="f9f93-107">Tür</span><span class="sxs-lookup"><span data-stu-id="f9f93-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9f93-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9f93-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f9f93-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9f93-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9f93-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9f93-110">Attributes</span></span>  
  
|<span data-ttu-id="f9f93-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9f93-111">Attribute</span></span>|<span data-ttu-id="f9f93-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9f93-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="f9f93-113">Paylaşım hizmeti için dinleme uç noktasındaki en fazla bekleyen eşzamanlı iş parçacığı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f9f93-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="f9f93-114">Varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f9f93-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="f9f93-115">Dağıtım için bekilebilecek en fazla bağlantı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f9f93-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="f9f93-116">Varsayılan değer 100'dür.</span><span class="sxs-lookup"><span data-stu-id="f9f93-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f9f93-117">Çerçeveleme <xref:System.TimeSpan> verilerini okumak ve alt çizgi bağlantılarından bağlantı dağıtma işlemini gerçekleştirmek için zaman aşımını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="f9f93-117">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="f9f93-118">Varsayılan değer "00:00:10" dır</span><span class="sxs-lookup"><span data-stu-id="f9f93-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9f93-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9f93-119">Child Elements</span></span>  
  
|<span data-ttu-id="f9f93-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9f93-120">Element</span></span>|<span data-ttu-id="f9f93-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9f93-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9f93-122">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="f9f93-122">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="f9f93-123">WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek `securityIdentifier` için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="f9f93-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9f93-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9f93-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f9f93-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9f93-125">Element</span></span>|<span data-ttu-id="f9f93-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9f93-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9f93-127">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="f9f93-127">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="f9f93-128">SMSvcHost. exe dinleyici işleminin yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f9f93-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9f93-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9f93-129">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
