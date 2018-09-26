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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47072802"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="fb7ee-102">&lt;kaldırma&gt; authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="fb7ee-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="fb7ee-103">Bir kimlik doğrulama modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fb7ee-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="fb7ee-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="fb7ee-104">\<configuration></span></span>  
<span data-ttu-id="fb7ee-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fb7ee-105">\<system.net></span></span>  
<span data-ttu-id="fb7ee-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="fb7ee-106">\<authenticationModules></span></span>  
<span data-ttu-id="fb7ee-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="fb7ee-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb7ee-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb7ee-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb7ee-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb7ee-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fb7ee-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb7ee-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb7ee-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb7ee-111">Attributes</span></span>  
  
|<span data-ttu-id="fb7ee-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="fb7ee-112">**Attribute**</span></span>|<span data-ttu-id="fb7ee-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="fb7ee-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="fb7ee-114">**Türü**</span><span class="sxs-lookup"><span data-stu-id="fb7ee-114">**type**</span></span>|<span data-ttu-id="fb7ee-115">Kimlik doğrulama modülünü kaldırmak için adı.</span><span class="sxs-lookup"><span data-stu-id="fb7ee-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb7ee-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb7ee-116">Child Elements</span></span>  
 <span data-ttu-id="fb7ee-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="fb7ee-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb7ee-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb7ee-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fb7ee-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="fb7ee-119">**Element**</span></span>|<span data-ttu-id="fb7ee-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="fb7ee-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fb7ee-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="fb7ee-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="fb7ee-122">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb7ee-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb7ee-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb7ee-123">Remarks</span></span>  
 <span data-ttu-id="fb7ee-124">`remove` , Daha önce yapılandırma dosyası veya yapılandırma hiyerarşideki daha yüksek bir düzeyde tanımlanan kimlik doğrulama modülü öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fb7ee-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="fb7ee-125">Değeri `type` özniteliği geçerli bir sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fb7ee-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fb7ee-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="fb7ee-126">Configuration Files</span></span>  
 <span data-ttu-id="fb7ee-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fb7ee-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb7ee-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb7ee-128">Example</span></span>  
 <span data-ttu-id="fb7ee-129">Aşağıdaki örnek, bir kimlik doğrulama modülü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fb7ee-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb7ee-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb7ee-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="fb7ee-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fb7ee-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
