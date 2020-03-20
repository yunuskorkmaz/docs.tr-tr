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
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154731"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="972e4-102">\<webRequestModules (Ağ Ayarları) için> Öğeyi kaldırın</span><span class="sxs-lookup"><span data-stu-id="972e4-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="972e4-103">Özel bir Web isteği modüllerini uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="972e4-103">Removes a custom Web request module from the application.</span></span>  
  
<span data-ttu-id="972e4-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="972e4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="972e4-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="972e4-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="972e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="972e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="972e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>kaldırmak**</span><span class="sxs-lookup"><span data-stu-id="972e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="972e4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="972e4-108">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="972e4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="972e4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="972e4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="972e4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="972e4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="972e4-111">Attributes</span></span>  
  
|<span data-ttu-id="972e4-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="972e4-112">**Attribute**</span></span>|<span data-ttu-id="972e4-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="972e4-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="972e4-114">Bu Web istek modülü tarafından işlenen istekler için URI öneki.</span><span class="sxs-lookup"><span data-stu-id="972e4-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="972e4-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="972e4-115">Child Elements</span></span>  
 <span data-ttu-id="972e4-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="972e4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="972e4-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="972e4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="972e4-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="972e4-118">**Element**</span></span>|<span data-ttu-id="972e4-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="972e4-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="972e4-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="972e4-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="972e4-121">Ağ ana bilgisayarlarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="972e4-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="972e4-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="972e4-122">Remarks</span></span>  
 <span data-ttu-id="972e4-123">Öğe, `remove` belirtilen URI öneki için kayıtlı Web isteği modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="972e4-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="972e4-124">Öznitelik değeri `prefix` geçerli bir URI'nin önde gelen karakterleri olmalıdır`http`- örneğin,`http://www.contoso.com`" ", veya " ".</span><span class="sxs-lookup"><span data-stu-id="972e4-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="972e4-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="972e4-125">Configuration Files</span></span>  
 <span data-ttu-id="972e4-126">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="972e4-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="972e4-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="972e4-127">Example</span></span>  

<span data-ttu-id="972e4-128">Aşağıdaki örnek, HTTP için varolan Web istek modüllerini kaldırır ve ardından HTTP `www.contoso.com`istekleri için yeni bir özel Web isteği modüllerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="972e4-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="972e4-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="972e4-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="972e4-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="972e4-130">Network Settings Schema</span></span>](index.md)
