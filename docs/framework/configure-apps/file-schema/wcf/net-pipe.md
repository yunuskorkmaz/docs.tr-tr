---
title: '&lt;NET.pipe&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5d68c2113b08065f7ec74ae68d7f0b5918cab0aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltnetpipegt"></a><span data-ttu-id="69738-102">&lt;NET.pipe&gt;</span><span class="sxs-lookup"><span data-stu-id="69738-102">&lt;net.pipe&gt;</span></span>
<span data-ttu-id="69738-103">Adlandırılmış kanal etkinleştirme adlandırılmış kanal bağlantısı ömrü yöneten ve Adlandırılmış Kanallar üzerinden gelmesini etkinleştirme isteklerini yürüten hizmeti, yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="69738-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="69738-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="69738-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="69738-105">\<NET.pipe ></span><span class="sxs-lookup"><span data-stu-id="69738-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69738-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69738-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
          <allowAccounts>  
             // LocalSystem account  
             <add securityIdentifier="S-1-5-18"/>  
             // LocalService account  
             <add securityIdentifier="S-1-5-19"/>  
             // Administrators account  
             <add securityIdentifier="S-1-5-20"/>  
             // Network Service account  
             <add securityIdentifier="S-1-5-32-544" />  
             // IIS_IUSRS account (Vista only)  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="69738-107">Tür</span><span class="sxs-lookup"><span data-stu-id="69738-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69738-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="69738-108">Attributes and Elements</span></span>  
 <span data-ttu-id="69738-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="69738-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69738-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="69738-110">Attributes</span></span>  
  
|<span data-ttu-id="69738-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="69738-111">Attribute</span></span>|<span data-ttu-id="69738-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69738-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="69738-113">Dinleme bitiş Paylaşım Hizmeti için en çok bekleyen eşzamanlı kabul iş parçacığı belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="69738-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="69738-114">Varsayılan değer 2'dir.</span><span class="sxs-lookup"><span data-stu-id="69738-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="69738-115">En fazla gönderim için bekleyebilirsiniz bağlantı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="69738-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="69738-116">Varsayılan değer 100'dür.</span><span class="sxs-lookup"><span data-stu-id="69738-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="69738-117">A `TimeSpan` çerçeveleme veri okumak ve altı çizili bağlantılarından bağlantı gönderme gerçekleştirmek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="69738-117">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="69738-118">Varsayılan değer "00: 00:10"</span><span class="sxs-lookup"><span data-stu-id="69738-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69738-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="69738-119">Child Elements</span></span>  
  
|<span data-ttu-id="69738-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="69738-120">Element</span></span>|<span data-ttu-id="69738-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69738-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69738-122">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="69738-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="69738-123">İçeren yapılandırma öğelerinin koleksiyonu bir `securityIdentifier` kullanıcı hesapları için işlemleri barındıran belirtmek için özniteliği [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir.</span><span class="sxs-lookup"><span data-stu-id="69738-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69738-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="69738-124">Parent Elements</span></span>  
  
|<span data-ttu-id="69738-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="69738-125">Element</span></span>|<span data-ttu-id="69738-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69738-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69738-127">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="69738-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="69738-128">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="69738-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69738-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69738-129">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
