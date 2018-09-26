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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d0da0fd2edae4687ea80b4a23cc82a25ead9cb7b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208587"
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="25893-102">&lt;kaldırma&gt; webRequestModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="25893-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="25893-103">Özel bir Web isteği modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="25893-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="25893-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="25893-104">\<configuration></span></span>  
<span data-ttu-id="25893-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="25893-105">\<system.net></span></span>  
<span data-ttu-id="25893-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="25893-106">\<webRequestModules></span></span>  
<span data-ttu-id="25893-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="25893-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25893-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25893-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25893-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="25893-109">Attributes and Elements</span></span>  
 <span data-ttu-id="25893-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25893-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25893-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25893-111">Attributes</span></span>  
  
|<span data-ttu-id="25893-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="25893-112">**Attribute**</span></span>|<span data-ttu-id="25893-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="25893-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="25893-114">Bu Web isteği modülü tarafından işlenen isteklerin için URI öneki.</span><span class="sxs-lookup"><span data-stu-id="25893-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25893-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="25893-115">Child Elements</span></span>  
 <span data-ttu-id="25893-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="25893-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25893-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="25893-117">Parent Elements</span></span>  
  
|<span data-ttu-id="25893-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="25893-118">**Element**</span></span>|<span data-ttu-id="25893-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="25893-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="25893-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="25893-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="25893-121">Ağ konaklarından bilgi istemek için modüller belirtir.</span><span class="sxs-lookup"><span data-stu-id="25893-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25893-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25893-122">Remarks</span></span>  
 <span data-ttu-id="25893-123">`remove` Belirtilen URI öneki kayıtlı Web isteği modülü öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="25893-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="25893-124">Değeri `prefix` özniteliği olmalıdır geçerli bir URI--Örneğin, "http", önde gelen karakterlerini veya "`http://www.contoso.com` ".</span><span class="sxs-lookup"><span data-stu-id="25893-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "http", or "`http://www.contoso.com` ".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="25893-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="25893-125">Configuration Files</span></span>  
 <span data-ttu-id="25893-126">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25893-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="25893-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="25893-127">Example</span></span>  
 <span data-ttu-id="25893-128">Aşağıdaki örnek, HTTP için mevcut Web isteği modülü kaldırır ve ardından yeni özel bir Web isteği modülü HTTP istekleri www.contoso.com için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="25893-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to www.contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25893-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25893-129">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="25893-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="25893-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
