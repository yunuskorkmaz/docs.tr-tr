---
title: '&lt;kaldırma&gt; webRequestModules (ağ ayarları) için'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: 2f787206c503c047a34383e12c5676296e39c1fe
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190755"
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="13db0-102">&lt;kaldırma&gt; webRequestModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="13db0-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="13db0-103">Özel bir Web isteği modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="13db0-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="13db0-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="13db0-104">\<configuration></span></span>  
<span data-ttu-id="13db0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="13db0-105">\<system.net></span></span>  
<span data-ttu-id="13db0-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="13db0-106">\<webRequestModules></span></span>  
<span data-ttu-id="13db0-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="13db0-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13db0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13db0-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13db0-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="13db0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="13db0-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13db0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13db0-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="13db0-111">Attributes</span></span>  
  
|<span data-ttu-id="13db0-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="13db0-112">**Attribute**</span></span>|<span data-ttu-id="13db0-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="13db0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="13db0-114">Bu Web isteği modülü tarafından işlenen isteklerin için URI öneki.</span><span class="sxs-lookup"><span data-stu-id="13db0-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13db0-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="13db0-115">Child Elements</span></span>  
 <span data-ttu-id="13db0-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="13db0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13db0-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="13db0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="13db0-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="13db0-118">**Element**</span></span>|<span data-ttu-id="13db0-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="13db0-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="13db0-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="13db0-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="13db0-121">Ağ konaklarından bilgi istemek için modüller belirtir.</span><span class="sxs-lookup"><span data-stu-id="13db0-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13db0-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13db0-122">Remarks</span></span>  
 <span data-ttu-id="13db0-123">`remove` Belirtilen URI öneki kayıtlı Web isteği modülü öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="13db0-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="13db0-124">Değeri `prefix` özniteliği olmalıdır geçerli bir URI'ın önde gelen karakter Örneğin, "`http`", veya "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="13db0-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="13db0-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="13db0-125">Configuration Files</span></span>  
 <span data-ttu-id="13db0-126">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="13db0-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13db0-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="13db0-127">Example</span></span>  

<span data-ttu-id="13db0-128">Aşağıdaki örnek, HTTP için mevcut Web isteği modülü kaldırır ve ardından kayıtları için yeni özel bir Web isteği modülü için HTTP istekleri `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="13db0-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13db0-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13db0-129">See Also</span></span>  
- <xref:System.Net.WebRequest>  
- [<span data-ttu-id="13db0-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="13db0-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
