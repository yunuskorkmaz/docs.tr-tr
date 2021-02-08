---
description: 'Daha fazla bilgi edinin: <remove> authenticationModules için öğesi (ağ ayarları)'
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
ms.openlocfilehash: 7c97cd20717e6e0945cf77ad6584b319120ec6a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804094"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="3ffb7-103">authenticationModules için \<remove> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="3ffb7-103">\<remove> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="3ffb7-104">Bir kimlik doğrulama modülünü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3ffb7-104">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="3ffb7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ffb7-105">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ffb7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ffb7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3ffb7-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3ffb7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ffb7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3ffb7-108">Attributes</span></span>  
  
|<span data-ttu-id="3ffb7-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="3ffb7-109">**Attribute**</span></span>|<span data-ttu-id="3ffb7-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="3ffb7-110">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="3ffb7-111">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="3ffb7-111">**type**</span></span>|<span data-ttu-id="3ffb7-112">Kaldırılacak kimlik doğrulama modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="3ffb7-112">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ffb7-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ffb7-113">Child Elements</span></span>  

 <span data-ttu-id="3ffb7-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="3ffb7-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ffb7-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ffb7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="3ffb7-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="3ffb7-116">**Element**</span></span>|<span data-ttu-id="3ffb7-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="3ffb7-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3ffb7-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="3ffb7-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="3ffb7-119">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ffb7-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ffb7-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ffb7-120">Remarks</span></span>  

 <span data-ttu-id="3ffb7-121">`remove`Öğesi yapılandırma hiyerarşisinde daha önce tanımlanan kimlik doğrulama modüllerini veya yapılandırma hiyerarşisinde daha yüksek bir düzeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3ffb7-121">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="3ffb7-122">`type`Özniteliğin değeri geçerli bir sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ffb7-122">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3ffb7-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="3ffb7-123">Configuration Files</span></span>  

 <span data-ttu-id="3ffb7-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ffb7-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ffb7-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ffb7-125">Example</span></span>  

 <span data-ttu-id="3ffb7-126">Aşağıdaki örnek bir kimlik doğrulama modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3ffb7-126">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ffb7-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ffb7-127">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="3ffb7-128">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="3ffb7-128">Network Settings Schema</span></span>](index.md)
