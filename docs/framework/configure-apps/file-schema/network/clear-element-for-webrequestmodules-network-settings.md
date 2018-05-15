---
title: '&lt;Clear&gt; öğesi webRequestModules (ağ ayarları) için'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4d89fbc757198f25219b8051bf77dbdeea0cef53
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="88cab-102">&lt;Clear&gt; öğesi webRequestModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="88cab-102">&lt;clear&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="88cab-103">Tüm kayıtlı Web isteği modülleri uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="88cab-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="88cab-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="88cab-104">\<configuration></span></span>  
<span data-ttu-id="88cab-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="88cab-105">\<system.net></span></span>  
<span data-ttu-id="88cab-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="88cab-106">\<webRequestModules></span></span>  
<span data-ttu-id="88cab-107">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="88cab-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88cab-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88cab-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88cab-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="88cab-109">Attributes and Elements</span></span>  
 <span data-ttu-id="88cab-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88cab-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88cab-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="88cab-111">Attributes</span></span>  
 <span data-ttu-id="88cab-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="88cab-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="88cab-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="88cab-113">Child Elements</span></span>  
 <span data-ttu-id="88cab-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="88cab-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88cab-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="88cab-115">Parent Elements</span></span>  
  
|<span data-ttu-id="88cab-116">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="88cab-116">**Element**</span></span>|<span data-ttu-id="88cab-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="88cab-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="88cab-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="88cab-118">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="88cab-119">Ağ ana bilgisayarlardan bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="88cab-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88cab-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88cab-120">Remarks</span></span>  
 <span data-ttu-id="88cab-121">`clear` Öğeyi yapılandırma dosyası veya yapılandırma hiyerarşisindeki daha yüksek düzeyde daha önce tanımlanan tüm kayıtlı Web isteği modülleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="88cab-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="88cab-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="88cab-122">Configuration Files</span></span>  
 <span data-ttu-id="88cab-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88cab-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88cab-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="88cab-124">Example</span></span>  
 <span data-ttu-id="88cab-125">Aşağıdaki örnek, tüm Web isteği modülleri temizler ve ardından HTTP için Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="88cab-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88cab-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88cab-126">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="88cab-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="88cab-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
