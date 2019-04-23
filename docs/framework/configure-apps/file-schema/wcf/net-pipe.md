---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 885cfad7be42f7c48b4c061f3293d667eb5d4ad8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103408"
---
# <a name="netpipe"></a><span data-ttu-id="d80c3-102">\<NET.pipe ></span><span class="sxs-lookup"><span data-stu-id="d80c3-102">\<net.pipe></span></span>
<span data-ttu-id="d80c3-103">Adlandırılmış kanal etkinleştirme adlandırılmış kanal bağlantısının yaşam yönetir ve Adlandırılmış Kanallar üzerinden erişen aktivasyon isteklerini işleyen hizmeti için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d80c3-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="d80c3-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="d80c3-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="d80c3-105">\<NET.pipe ></span><span class="sxs-lookup"><span data-stu-id="d80c3-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d80c3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d80c3-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="d80c3-107">Tür</span><span class="sxs-lookup"><span data-stu-id="d80c3-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d80c3-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d80c3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d80c3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d80c3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d80c3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d80c3-110">Attributes</span></span>  
  
|<span data-ttu-id="d80c3-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d80c3-111">Attribute</span></span>|<span data-ttu-id="d80c3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d80c3-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="d80c3-113">Hizmetler için olan uç noktaları en fazla bekleyen eşzamanlı kabul iş parçacığı belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d80c3-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="d80c3-114">Varsayılan değer 2'dir.</span><span class="sxs-lookup"><span data-stu-id="d80c3-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="d80c3-115">Gönderme için bekleyebileceği bağlantı maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d80c3-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="d80c3-116">Varsayılan değer 100'dür.</span><span class="sxs-lookup"><span data-stu-id="d80c3-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d80c3-117">A <xref:System.TimeSpan> ve çerçeveleme verilerini okumak ve altı çizili bağlantılardan bağlantı dağıtımını gerçekleştirmek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d80c3-117">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="d80c3-118">Varsayılan değer "00: 00:10"</span><span class="sxs-lookup"><span data-stu-id="d80c3-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d80c3-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d80c3-119">Child Elements</span></span>  
  
|<span data-ttu-id="d80c3-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="d80c3-120">Element</span></span>|<span data-ttu-id="d80c3-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d80c3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d80c3-122">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="d80c3-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="d80c3-123">Bir koleksiyon içeren yapılandırma öğelerinin bir `securityIdentifier` barındıran WCF hizmetleri ve Paylaşım Hizmeti bağlantı erişim izni verilen işlemleri için kullanıcı hesabı belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d80c3-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d80c3-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d80c3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d80c3-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="d80c3-125">Element</span></span>|<span data-ttu-id="d80c3-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d80c3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d80c3-127">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="d80c3-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="d80c3-128">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d80c3-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d80c3-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d80c3-129">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
