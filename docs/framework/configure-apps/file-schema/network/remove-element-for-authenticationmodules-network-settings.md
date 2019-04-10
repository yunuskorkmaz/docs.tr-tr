---
title: <remove> AuthenticationModules (ağ ayarları) için
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
ms.openlocfilehash: 0eb3ef7db422d5cbbe70bd5633798b8d3787452d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125259"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="09221-102">\<kaldırma > authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="09221-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="09221-103">Bir kimlik doğrulama modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="09221-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="09221-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="09221-104">\<configuration></span></span>  
<span data-ttu-id="09221-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="09221-105">\<system.net></span></span>  
<span data-ttu-id="09221-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="09221-106">\<authenticationModules></span></span>  
<span data-ttu-id="09221-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="09221-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09221-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09221-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09221-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="09221-109">Attributes and Elements</span></span>  
 <span data-ttu-id="09221-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="09221-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09221-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="09221-111">Attributes</span></span>  
  
|**<span data-ttu-id="09221-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="09221-112">Attribute</span></span>**|**<span data-ttu-id="09221-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09221-113">Description</span></span>**|  
|-------------------|---------------------|  
|**<span data-ttu-id="09221-114"> türü</span><span class="sxs-lookup"><span data-stu-id="09221-114">type</span></span>**|<span data-ttu-id="09221-115">Kimlik doğrulama modülünü kaldırmak için adı.</span><span class="sxs-lookup"><span data-stu-id="09221-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09221-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="09221-116">Child Elements</span></span>  
 <span data-ttu-id="09221-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="09221-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09221-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="09221-118">Parent Elements</span></span>  
  
|**<span data-ttu-id="09221-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="09221-119">Element</span></span>**|**<span data-ttu-id="09221-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09221-120">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="09221-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="09221-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="09221-122">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="09221-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09221-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09221-123">Remarks</span></span>  
 <span data-ttu-id="09221-124">`remove` , Daha önce yapılandırma dosyası veya yapılandırma hiyerarşideki daha yüksek bir düzeyde tanımlanan kimlik doğrulama modülü öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="09221-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="09221-125">Değeri `type` özniteliği geçerli bir sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="09221-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="09221-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="09221-126">Configuration Files</span></span>  
 <span data-ttu-id="09221-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="09221-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09221-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="09221-128">Example</span></span>  
 <span data-ttu-id="09221-129">Aşağıdaki örnek, bir kimlik doğrulama modülü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="09221-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09221-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09221-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="09221-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="09221-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
