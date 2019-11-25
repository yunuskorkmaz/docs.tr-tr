---
title: webRequestModules için <clear> Öğesi (Ağ Ayarları)
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
ms.openlocfilehash: 5832d120824df75d374fc94cb0aa4e08189cb965
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088496"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="f3fdd-102">webRequestModules için \<Clear > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="f3fdd-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="f3fdd-103">Tüm kayıtlı Web isteği modüllerini uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f3fdd-103">Removes all registered Web request modules from the application.</span></span>  

<span data-ttu-id="f3fdd-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f3fdd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f3fdd-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="f3fdd-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="f3fdd-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webRequestModules**](webrequestmodules-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="f3fdd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="f3fdd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="f3fdd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f3fdd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3fdd-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3fdd-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3fdd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f3fdd-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3fdd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3fdd-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f3fdd-111">Attributes</span></span>  
 <span data-ttu-id="f3fdd-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="f3fdd-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3fdd-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3fdd-113">Child Elements</span></span>  
 <span data-ttu-id="f3fdd-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="f3fdd-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3fdd-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3fdd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f3fdd-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="f3fdd-116">**Element**</span></span>|<span data-ttu-id="f3fdd-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f3fdd-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f3fdd-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="f3fdd-118">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="f3fdd-119">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3fdd-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3fdd-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3fdd-120">Remarks</span></span>  
 <span data-ttu-id="f3fdd-121">`clear` öğesi, daha önce yapılandırma dosyasında veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan tüm kayıtlı Web isteği modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f3fdd-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f3fdd-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f3fdd-122">Configuration Files</span></span>  
 <span data-ttu-id="f3fdd-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3fdd-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3fdd-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3fdd-124">Example</span></span>  
 <span data-ttu-id="f3fdd-125">Aşağıdaki örnek, tüm Web isteği modüllerini temizler ve ardından HTTP için bir Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f3fdd-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3fdd-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3fdd-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="f3fdd-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f3fdd-127">Network Settings Schema</span></span>](index.md)
