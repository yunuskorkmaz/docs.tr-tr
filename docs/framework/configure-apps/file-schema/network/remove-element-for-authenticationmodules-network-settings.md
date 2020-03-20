---
title: authenticationModules için <remove> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: d171fea193bbae068e69b8976abb8e56a5623f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154783"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="339c8-102">\<kimlik doğrulama modülleri için> Öğesi kaldırma (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="339c8-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="339c8-103">Uygulamadan bir kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="339c8-103">Removes an authentication module from the application.</span></span>  

<span data-ttu-id="339c8-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="339c8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="339c8-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="339c8-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="339c8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kimlik doğrulamaModülleri>**](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="339c8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="339c8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>kaldırmak**</span><span class="sxs-lookup"><span data-stu-id="339c8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="339c8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="339c8-108">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="339c8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="339c8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="339c8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="339c8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="339c8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="339c8-111">Attributes</span></span>  
  
|<span data-ttu-id="339c8-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="339c8-112">**Attribute**</span></span>|<span data-ttu-id="339c8-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="339c8-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="339c8-114">**Türü**</span><span class="sxs-lookup"><span data-stu-id="339c8-114">**type**</span></span>|<span data-ttu-id="339c8-115">Kaldırılacak kimlik doğrulama modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="339c8-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="339c8-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="339c8-116">Child Elements</span></span>  
 <span data-ttu-id="339c8-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="339c8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="339c8-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="339c8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="339c8-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="339c8-119">**Element**</span></span>|<span data-ttu-id="339c8-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="339c8-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="339c8-121">kimlik doğrulamaModülleri</span><span class="sxs-lookup"><span data-stu-id="339c8-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="339c8-122">Ağ isteklerini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="339c8-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="339c8-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="339c8-123">Remarks</span></span>  
 <span data-ttu-id="339c8-124">Öğe, `remove` yapılandırma dosyasında veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde daha önce tanımlanan kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="339c8-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="339c8-125">Öznitelik için `type` değer geçerli bir sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="339c8-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="339c8-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="339c8-126">Configuration Files</span></span>  
 <span data-ttu-id="339c8-127">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="339c8-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="339c8-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="339c8-128">Example</span></span>  
 <span data-ttu-id="339c8-129">Aşağıdaki örnek, kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="339c8-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="339c8-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="339c8-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="339c8-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="339c8-131">Network Settings Schema</span></span>](index.md)
