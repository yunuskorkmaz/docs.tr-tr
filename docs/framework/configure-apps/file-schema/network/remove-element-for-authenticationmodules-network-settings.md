---
title: '&lt;kaldırma&gt; authenticationModules (ağ ayarları) için'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 332f8eb4fb1a5a02df76c5745522037b029a2407
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780654"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="8ab68-102">&lt;kaldırma&gt; authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="8ab68-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="8ab68-103">Bir kimlik doğrulama modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8ab68-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="8ab68-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8ab68-104">\<configuration></span></span>  
<span data-ttu-id="8ab68-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8ab68-105">\<system.net></span></span>  
<span data-ttu-id="8ab68-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="8ab68-106">\<authenticationModules></span></span>  
<span data-ttu-id="8ab68-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="8ab68-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ab68-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ab68-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ab68-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ab68-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8ab68-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ab68-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ab68-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ab68-111">Attributes</span></span>  
  
|<span data-ttu-id="8ab68-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="8ab68-112">**Attribute**</span></span>|<span data-ttu-id="8ab68-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8ab68-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="8ab68-114">**Türü**</span><span class="sxs-lookup"><span data-stu-id="8ab68-114">**type**</span></span>|<span data-ttu-id="8ab68-115">Kimlik doğrulama modülünü kaldırmak için adı.</span><span class="sxs-lookup"><span data-stu-id="8ab68-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ab68-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ab68-116">Child Elements</span></span>  
 <span data-ttu-id="8ab68-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ab68-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ab68-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ab68-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8ab68-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="8ab68-119">**Element**</span></span>|<span data-ttu-id="8ab68-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8ab68-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8ab68-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="8ab68-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="8ab68-122">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ab68-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ab68-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ab68-123">Remarks</span></span>  
 <span data-ttu-id="8ab68-124">`remove` , Daha önce yapılandırma dosyası veya yapılandırma hiyerarşideki daha yüksek bir düzeyde tanımlanan kimlik doğrulama modülü öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8ab68-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="8ab68-125">Değeri `type` özniteliği geçerli bir sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ab68-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8ab68-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="8ab68-126">Configuration Files</span></span>  
 <span data-ttu-id="8ab68-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ab68-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ab68-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ab68-128">Example</span></span>  
 <span data-ttu-id="8ab68-129">Aşağıdaki örnek, bir kimlik doğrulama modülü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8ab68-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ab68-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ab68-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="8ab68-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8ab68-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
