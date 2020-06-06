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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154783"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="05ef5-102">authenticationModules için \<remove> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="05ef5-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="05ef5-103">Bir kimlik doğrulama modülünü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="05ef5-103">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="05ef5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05ef5-104">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05ef5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="05ef5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="05ef5-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05ef5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05ef5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="05ef5-107">Attributes</span></span>  
  
|<span data-ttu-id="05ef5-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="05ef5-108">**Attribute**</span></span>|<span data-ttu-id="05ef5-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="05ef5-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="05ef5-110">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="05ef5-110">**type**</span></span>|<span data-ttu-id="05ef5-111">Kaldırılacak kimlik doğrulama modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="05ef5-111">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05ef5-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="05ef5-112">Child Elements</span></span>  
 <span data-ttu-id="05ef5-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="05ef5-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05ef5-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="05ef5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="05ef5-115">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="05ef5-115">**Element**</span></span>|<span data-ttu-id="05ef5-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="05ef5-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="05ef5-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="05ef5-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="05ef5-118">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="05ef5-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05ef5-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05ef5-119">Remarks</span></span>  
 <span data-ttu-id="05ef5-120">`remove`Öğesi yapılandırma hiyerarşisinde daha önce tanımlanan kimlik doğrulama modüllerini veya yapılandırma hiyerarşisinde daha yüksek bir düzeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="05ef5-120">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="05ef5-121">`type`Özniteliğin değeri geçerli bir sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05ef5-121">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="05ef5-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="05ef5-122">Configuration Files</span></span>  
 <span data-ttu-id="05ef5-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05ef5-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05ef5-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="05ef5-124">Example</span></span>  
 <span data-ttu-id="05ef5-125">Aşağıdaki örnek bir kimlik doğrulama modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="05ef5-125">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05ef5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05ef5-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="05ef5-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="05ef5-127">Network Settings Schema</span></span>](index.md)
