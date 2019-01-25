---
title: '&lt;NET.pipe&gt;'
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 7997894bfad8d5bf874a7f52d2cade7526375b13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715302"
---
# <a name="ltnetpipegt"></a><span data-ttu-id="89bc6-102">&lt;NET.pipe&gt;</span><span class="sxs-lookup"><span data-stu-id="89bc6-102">&lt;net.pipe&gt;</span></span>
<span data-ttu-id="89bc6-103">Adlandırılmış kanal etkinleştirme adlandırılmış kanal bağlantısının yaşam yönetir ve Adlandırılmış Kanallar üzerinden erişen aktivasyon isteklerini işleyen hizmeti için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="89bc6-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="89bc6-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="89bc6-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="89bc6-105">\<NET.pipe ></span><span class="sxs-lookup"><span data-stu-id="89bc6-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89bc6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89bc6-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="89bc6-107">Tür</span><span class="sxs-lookup"><span data-stu-id="89bc6-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89bc6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89bc6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="89bc6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89bc6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89bc6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89bc6-110">Attributes</span></span>  
  
|<span data-ttu-id="89bc6-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89bc6-111">Attribute</span></span>|<span data-ttu-id="89bc6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89bc6-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="89bc6-113">Hizmetler için olan uç noktaları en fazla bekleyen eşzamanlı kabul iş parçacığı belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="89bc6-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="89bc6-114">Varsayılan değer 2'dir.</span><span class="sxs-lookup"><span data-stu-id="89bc6-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="89bc6-115">Gönderme için bekleyebileceği bağlantı maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="89bc6-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="89bc6-116">Varsayılan değer 100'dür.</span><span class="sxs-lookup"><span data-stu-id="89bc6-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="89bc6-117">A `TimeSpan` ve çerçeveleme verilerini okumak ve altı çizili bağlantılardan bağlantı dağıtımını gerçekleştirmek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="89bc6-117">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="89bc6-118">Varsayılan değer "00: 00:10"</span><span class="sxs-lookup"><span data-stu-id="89bc6-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89bc6-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89bc6-119">Child Elements</span></span>  
  
|<span data-ttu-id="89bc6-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="89bc6-120">Element</span></span>|<span data-ttu-id="89bc6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89bc6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89bc6-122">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="89bc6-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="89bc6-123">Bir koleksiyon içeren yapılandırma öğelerinin bir `securityIdentifier` barındıran WCF hizmetleri ve Paylaşım Hizmeti bağlantı erişim izni verilen işlemleri için kullanıcı hesabı belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="89bc6-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89bc6-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89bc6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="89bc6-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="89bc6-125">Element</span></span>|<span data-ttu-id="89bc6-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89bc6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89bc6-127">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="89bc6-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="89bc6-128">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="89bc6-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89bc6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89bc6-129">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
