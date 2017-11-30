---
title: "&lt;Clear&gt; öğesi authenticationModules (ağ ayarları) için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f056894148177e6b540fd45569140a996b6b888f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="27a06-102">&lt;Clear&gt; öğesi authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="27a06-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="27a06-103">Uygulamadaki tüm kimlik doğrulama modülleri temizler.</span><span class="sxs-lookup"><span data-stu-id="27a06-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="27a06-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="27a06-104">\<configuration></span></span>  
<span data-ttu-id="27a06-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="27a06-105">\<system.net></span></span>  
<span data-ttu-id="27a06-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="27a06-106">\<authenticationModules></span></span>  
<span data-ttu-id="27a06-107">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="27a06-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a06-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27a06-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27a06-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="27a06-109">Attributes and Elements</span></span>  
 <span data-ttu-id="27a06-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="27a06-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27a06-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="27a06-111">Attributes</span></span>  
 <span data-ttu-id="27a06-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="27a06-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="27a06-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="27a06-113">Child Elements</span></span>  
 <span data-ttu-id="27a06-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="27a06-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27a06-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="27a06-115">Parent Elements</span></span>  
  
|<span data-ttu-id="27a06-116">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="27a06-116">**Element**</span></span>|<span data-ttu-id="27a06-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="27a06-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="27a06-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="27a06-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="27a06-119">Ağ isteklerine kimlik doğrulaması için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="27a06-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27a06-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27a06-120">Remarks</span></span>  
 <span data-ttu-id="27a06-121">`clear` Öğeyi yapılandırma dosyası veya yapılandırma hiyerarşisindeki daha yüksek düzeyde daha önce tanımlanan tüm kimlik doğrulama modülleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="27a06-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="27a06-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="27a06-122">Configuration Files</span></span>  
 <span data-ttu-id="27a06-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="27a06-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27a06-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="27a06-124">Example</span></span>  
 <span data-ttu-id="27a06-125">Aşağıdaki örnek, tüm yapılandırılmış kimlik doğrulaması modülleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="27a06-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27a06-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27a06-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="27a06-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="27a06-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
