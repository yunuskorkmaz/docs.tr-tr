---
title: '&lt;kaldırma&gt; öğesi webRequestModules (ağ ayarları) için'
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
manager: markl
ms.openlocfilehash: e20d414b3be41fc175037c6691518adf6a424b69
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743033"
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="e6ba2-102">&lt;kaldırma&gt; öğesi webRequestModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="e6ba2-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="e6ba2-103">Özel bir Web isteği modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e6ba2-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="e6ba2-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e6ba2-104">\<configuration></span></span>  
<span data-ttu-id="e6ba2-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e6ba2-105">\<system.net></span></span>  
<span data-ttu-id="e6ba2-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="e6ba2-106">\<webRequestModules></span></span>  
<span data-ttu-id="e6ba2-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="e6ba2-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ba2-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6ba2-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6ba2-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6ba2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e6ba2-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6ba2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6ba2-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6ba2-111">Attributes</span></span>  
  
|<span data-ttu-id="e6ba2-112">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="e6ba2-112">**Attribute**</span></span>|<span data-ttu-id="e6ba2-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e6ba2-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="e6ba2-114">Bu Web isteği modülü tarafından işlenen isteklerin için URI öneki.</span><span class="sxs-lookup"><span data-stu-id="e6ba2-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6ba2-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6ba2-115">Child Elements</span></span>  
 <span data-ttu-id="e6ba2-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="e6ba2-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6ba2-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6ba2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e6ba2-118">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="e6ba2-118">**Element**</span></span>|<span data-ttu-id="e6ba2-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e6ba2-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e6ba2-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="e6ba2-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="e6ba2-121">Ağ ana bilgisayarlardan bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6ba2-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6ba2-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6ba2-122">Remarks</span></span>  
 <span data-ttu-id="e6ba2-123">`remove` Öğeyi belirtilen URI öneki için kayıtlı Web isteği modülü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e6ba2-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="e6ba2-124">Değeri `prefix` özniteliği geçerli bir URI--Örneğin, "http", baştaki karakterleri olmalıdır veya "http://www.contoso.com".</span><span class="sxs-lookup"><span data-stu-id="e6ba2-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "http", or "http://www.contoso.com".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e6ba2-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e6ba2-125">Configuration Files</span></span>  
 <span data-ttu-id="e6ba2-126">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6ba2-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6ba2-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6ba2-127">Example</span></span>  
 <span data-ttu-id="e6ba2-128">Aşağıdaki örnek, HTTP için var olan bir Web isteği modül kaldırır ve ardından yeni özel bir Web isteği modülü HTTP istekleri www.contoso.com için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e6ba2-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to www.contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6ba2-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6ba2-129">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="e6ba2-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e6ba2-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
