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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088496"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="5904e-102">webRequestModules için \<clear> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="5904e-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="5904e-103">Tüm kayıtlı Web isteği modüllerini uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5904e-103">Removes all registered Web request modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="5904e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5904e-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5904e-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5904e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5904e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5904e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5904e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5904e-107">Attributes</span></span>  
 <span data-ttu-id="5904e-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="5904e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5904e-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5904e-109">Child Elements</span></span>  
 <span data-ttu-id="5904e-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="5904e-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5904e-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5904e-111">Parent Elements</span></span>  
  
|<span data-ttu-id="5904e-112">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="5904e-112">**Element**</span></span>|<span data-ttu-id="5904e-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5904e-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5904e-114">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="5904e-114">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="5904e-115">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5904e-115">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5904e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5904e-116">Remarks</span></span>  
 <span data-ttu-id="5904e-117">`clear`Öğesi, daha önce yapılandırma dosyasında veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan tüm kayıtlı Web isteği modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5904e-117">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5904e-118">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5904e-118">Configuration Files</span></span>  
 <span data-ttu-id="5904e-119">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5904e-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5904e-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="5904e-120">Example</span></span>  
 <span data-ttu-id="5904e-121">Aşağıdaki örnek, tüm Web isteği modüllerini temizler ve ardından HTTP için bir Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5904e-121">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5904e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5904e-122">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="5904e-123">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5904e-123">Network Settings Schema</span></span>](index.md)
