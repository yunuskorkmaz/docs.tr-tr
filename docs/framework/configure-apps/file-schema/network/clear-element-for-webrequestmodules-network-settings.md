---
description: 'Daha fazla bilgi edinin: <clear> webRequestModules için öğesi (ağ ayarları)'
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
ms.openlocfilehash: 0782bf9edeafed2d61a368c3f6a8b37ef226c990
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740424"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="6aff1-103">webRequestModules için \<clear> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="6aff1-103">\<clear> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="6aff1-104">Tüm kayıtlı Web isteği modüllerini uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6aff1-104">Removes all registered Web request modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="6aff1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6aff1-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6aff1-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6aff1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6aff1-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6aff1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6aff1-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6aff1-108">Attributes</span></span>  

 <span data-ttu-id="6aff1-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="6aff1-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6aff1-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6aff1-110">Child Elements</span></span>  

 <span data-ttu-id="6aff1-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="6aff1-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6aff1-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6aff1-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6aff1-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="6aff1-113">**Element**</span></span>|<span data-ttu-id="6aff1-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6aff1-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6aff1-115">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="6aff1-115">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="6aff1-116">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6aff1-116">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6aff1-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6aff1-117">Remarks</span></span>  

 <span data-ttu-id="6aff1-118">`clear`Öğesi, daha önce yapılandırma dosyasında veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan tüm kayıtlı Web isteği modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6aff1-118">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6aff1-119">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6aff1-119">Configuration Files</span></span>  

 <span data-ttu-id="6aff1-120">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6aff1-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6aff1-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="6aff1-121">Example</span></span>  

 <span data-ttu-id="6aff1-122">Aşağıdaki örnek, tüm Web isteği modüllerini temizler ve ardından HTTP için bir Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6aff1-122">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6aff1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6aff1-123">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="6aff1-124">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6aff1-124">Network Settings Schema</span></span>](index.md)
