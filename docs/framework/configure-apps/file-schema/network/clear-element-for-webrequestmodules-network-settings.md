---
title: "&lt;Clear&gt; öğesi webRequestModules (ağ ayarları) için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c88792663b07ace7250b6ee4065e60d6cfb90afd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="fbfe0-102">&lt;Clear&gt; öğesi webRequestModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="fbfe0-102">&lt;clear&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="fbfe0-103">Tüm kayıtlı Web isteği modülleri uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="fbfe0-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="fbfe0-104">\<configuration></span></span>  
<span data-ttu-id="fbfe0-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="fbfe0-105">\<system.net></span></span>  
<span data-ttu-id="fbfe0-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="fbfe0-106">\<webRequestModules></span></span>  
<span data-ttu-id="fbfe0-107">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="fbfe0-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbfe0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fbfe0-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbfe0-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbfe0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fbfe0-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbfe0-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fbfe0-111">Attributes</span></span>  
 <span data-ttu-id="fbfe0-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fbfe0-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbfe0-113">Child Elements</span></span>  
 <span data-ttu-id="fbfe0-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fbfe0-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbfe0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fbfe0-116">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="fbfe0-116">**Element**</span></span>|<span data-ttu-id="fbfe0-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="fbfe0-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fbfe0-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="fbfe0-118">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="fbfe0-119">Ağ ana bilgisayarlardan bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbfe0-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fbfe0-120">Remarks</span></span>  
 <span data-ttu-id="fbfe0-121">`clear` Öğeyi yapılandırma dosyası veya yapılandırma hiyerarşisindeki daha yüksek düzeyde daha önce tanımlanan tüm kayıtlı Web isteği modülleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fbfe0-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="fbfe0-122">Configuration Files</span></span>  
 <span data-ttu-id="fbfe0-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbfe0-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbfe0-124">Example</span></span>  
 <span data-ttu-id="fbfe0-125">Aşağıdaki örnek, tüm Web isteği modülleri temizler ve ardından HTTP için Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbfe0-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-126">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="fbfe0-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fbfe0-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
