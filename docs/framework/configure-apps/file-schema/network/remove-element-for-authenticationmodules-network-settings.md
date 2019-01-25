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
ms.openlocfilehash: 20d90c4554f9718651070456f6d4a14475d88bf6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651584"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="ffc60-102">&lt;kaldırma&gt; authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="ffc60-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="ffc60-103">Bir kimlik doğrulama modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ffc60-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="ffc60-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="ffc60-104">\<configuration></span></span>  
<span data-ttu-id="ffc60-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="ffc60-105">\<system.net></span></span>  
<span data-ttu-id="ffc60-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="ffc60-106">\<authenticationModules></span></span>  
<span data-ttu-id="ffc60-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="ffc60-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffc60-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ffc60-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffc60-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ffc60-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ffc60-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ffc60-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffc60-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ffc60-111">Attributes</span></span>  
  
|<span data-ttu-id="ffc60-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="ffc60-112">**Attribute**</span></span>|<span data-ttu-id="ffc60-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="ffc60-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="ffc60-114">**type**</span><span class="sxs-lookup"><span data-stu-id="ffc60-114">**type**</span></span>|<span data-ttu-id="ffc60-115">Kimlik doğrulama modülünü kaldırmak için adı.</span><span class="sxs-lookup"><span data-stu-id="ffc60-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ffc60-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ffc60-116">Child Elements</span></span>  
 <span data-ttu-id="ffc60-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="ffc60-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ffc60-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ffc60-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ffc60-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="ffc60-119">**Element**</span></span>|<span data-ttu-id="ffc60-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="ffc60-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ffc60-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="ffc60-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="ffc60-122">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffc60-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffc60-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffc60-123">Remarks</span></span>  
 <span data-ttu-id="ffc60-124">`remove` , Daha önce yapılandırma dosyası veya yapılandırma hiyerarşideki daha yüksek bir düzeyde tanımlanan kimlik doğrulama modülü öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ffc60-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="ffc60-125">Değeri `type` özniteliği geçerli bir sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffc60-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ffc60-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="ffc60-126">Configuration Files</span></span>  
 <span data-ttu-id="ffc60-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ffc60-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffc60-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="ffc60-128">Example</span></span>  
 <span data-ttu-id="ffc60-129">Aşağıdaki örnek, bir kimlik doğrulama modülü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ffc60-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffc60-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffc60-130">See also</span></span>
- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="ffc60-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ffc60-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
