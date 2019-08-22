---
title: webRequestModules için <remove> Öğesi (Ağ Ayarları)
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
ms.openlocfilehash: 20a586e945a889d1fd8a8d4c5c09c8b790c56fc3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664025"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="73188-102">\<webRequestModules için > öğesini kaldır (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="73188-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="73188-103">Uygulamadan özel bir Web istek modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="73188-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="73188-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="73188-104">\<configuration></span></span>  
<span data-ttu-id="73188-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="73188-105">\<system.net></span></span>  
<span data-ttu-id="73188-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="73188-106">\<webRequestModules></span></span>  
<span data-ttu-id="73188-107">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="73188-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73188-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73188-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73188-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73188-109">Attributes and Elements</span></span>  
 <span data-ttu-id="73188-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73188-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73188-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73188-111">Attributes</span></span>  
  
|<span data-ttu-id="73188-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="73188-112">**Attribute**</span></span>|<span data-ttu-id="73188-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="73188-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="73188-114">Bu Web isteği modülü tarafından işlenen istekler için URI ön eki.</span><span class="sxs-lookup"><span data-stu-id="73188-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73188-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73188-115">Child Elements</span></span>  
 <span data-ttu-id="73188-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="73188-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73188-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73188-117">Parent Elements</span></span>  
  
|<span data-ttu-id="73188-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="73188-118">**Element**</span></span>|<span data-ttu-id="73188-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="73188-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="73188-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="73188-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="73188-121">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="73188-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73188-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73188-122">Remarks</span></span>  
 <span data-ttu-id="73188-123">`remove` Öğesi, belirtilen URI ön eki için kayıtlı Web isteği modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="73188-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="73188-124">`prefix` Özniteliğin değeri geçerli bir URI 'nin baştaki karakterleri olmalıdır--örneğin, "`http`" veya "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="73188-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="73188-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="73188-125">Configuration Files</span></span>  
 <span data-ttu-id="73188-126">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73188-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73188-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="73188-127">Example</span></span>  

<span data-ttu-id="73188-128">Aşağıdaki örnek, HTTP için mevcut Web isteği modülünü kaldırır ve ardından HTTP istekleri `www.contoso.com`için yeni bir özel Web istek modülünü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="73188-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="73188-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73188-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="73188-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="73188-130">Network Settings Schema</span></span>](index.md)
