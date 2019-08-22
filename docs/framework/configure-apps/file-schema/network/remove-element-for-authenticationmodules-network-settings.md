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
ms.openlocfilehash: 7f923ce73760fa42a2c435d346f9d1097a5ed82f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664048"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="0a92b-102">\<authenticationModules için > öğesini kaldır (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="0a92b-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="0a92b-103">Bir kimlik doğrulama modülünü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0a92b-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="0a92b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0a92b-104">\<configuration></span></span>  
<span data-ttu-id="0a92b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0a92b-105">\<system.net></span></span>  
<span data-ttu-id="0a92b-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="0a92b-106">\<authenticationModules></span></span>  
<span data-ttu-id="0a92b-107">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="0a92b-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a92b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a92b-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a92b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a92b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0a92b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0a92b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a92b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0a92b-111">Attributes</span></span>  
  
|<span data-ttu-id="0a92b-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="0a92b-112">**Attribute**</span></span>|<span data-ttu-id="0a92b-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0a92b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="0a92b-114">**type**</span><span class="sxs-lookup"><span data-stu-id="0a92b-114">**type**</span></span>|<span data-ttu-id="0a92b-115">Kaldırılacak kimlik doğrulama modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="0a92b-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a92b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a92b-116">Child Elements</span></span>  
 <span data-ttu-id="0a92b-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="0a92b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a92b-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a92b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0a92b-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="0a92b-119">**Element**</span></span>|<span data-ttu-id="0a92b-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0a92b-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0a92b-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="0a92b-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="0a92b-122">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a92b-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a92b-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a92b-123">Remarks</span></span>  
 <span data-ttu-id="0a92b-124">`remove` Öğesi yapılandırma hiyerarşisinde daha önce tanımlanan kimlik doğrulama modüllerini veya yapılandırma hiyerarşisinde daha yüksek bir düzeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0a92b-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="0a92b-125">`type` Özniteliğin değeri geçerli bir sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a92b-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0a92b-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="0a92b-126">Configuration Files</span></span>  
 <span data-ttu-id="0a92b-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a92b-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a92b-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a92b-128">Example</span></span>  
 <span data-ttu-id="0a92b-129">Aşağıdaki örnek bir kimlik doğrulama modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0a92b-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a92b-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a92b-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="0a92b-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0a92b-131">Network Settings Schema</span></span>](index.md)
