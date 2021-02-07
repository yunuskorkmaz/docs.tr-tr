---
description: 'Daha fazla bilgi edinin: <remove> webRequestModules için öğesi (ağ ayarları)'
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
ms.openlocfilehash: db65c91417af2538e27b65e0ae28d06a6bfcde0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713006"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="8c5c6-103">webRequestModules için \<remove> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="8c5c6-103">\<remove> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="8c5c6-104">Uygulamadan özel bir Web istek modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8c5c6-104">Removes a custom Web request module from the application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**
  
## <a name="syntax"></a><span data-ttu-id="8c5c6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8c5c6-105">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c5c6-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c5c6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="8c5c6-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8c5c6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c5c6-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8c5c6-108">Attributes</span></span>  
  
|<span data-ttu-id="8c5c6-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="8c5c6-109">**Attribute**</span></span>|<span data-ttu-id="8c5c6-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8c5c6-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="8c5c6-111">Bu Web isteği modülü tarafından işlenen istekler için URI ön eki.</span><span class="sxs-lookup"><span data-stu-id="8c5c6-111">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c5c6-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c5c6-112">Child Elements</span></span>  

 <span data-ttu-id="8c5c6-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="8c5c6-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c5c6-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8c5c6-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8c5c6-115">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="8c5c6-115">**Element**</span></span>|<span data-ttu-id="8c5c6-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8c5c6-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8c5c6-117">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="8c5c6-117">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="8c5c6-118">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8c5c6-118">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c5c6-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c5c6-119">Remarks</span></span>  

 <span data-ttu-id="8c5c6-120">`remove`Öğesi, BELIRTILEN URI ön eki için kayıtlı Web isteği modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8c5c6-120">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="8c5c6-121">`prefix`Özniteliğin değeri geçerli BIR URI 'nin baştaki karakterleri olmalıdır--örneğin, " `http` " veya " `http://www.contoso.com` ".</span><span class="sxs-lookup"><span data-stu-id="8c5c6-121">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8c5c6-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="8c5c6-122">Configuration Files</span></span>  

 <span data-ttu-id="8c5c6-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8c5c6-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c5c6-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c5c6-124">Example</span></span>  

<span data-ttu-id="8c5c6-125">Aşağıdaki örnek, HTTP için mevcut Web isteği modülünü kaldırır ve ardından HTTP istekleri için yeni bir özel Web istek modülünü kaydeder `www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="8c5c6-125">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="8c5c6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c5c6-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="8c5c6-127">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="8c5c6-127">Network Settings Schema</span></span>](index.md)
