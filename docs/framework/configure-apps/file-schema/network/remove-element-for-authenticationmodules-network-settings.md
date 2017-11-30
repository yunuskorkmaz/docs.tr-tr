---
title: "&lt;kaldırma&gt; öğesi authenticationModules (ağ ayarları) için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: eb8490241d4ec8a34a76aa6087c1f4d27d5cebb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="74f14-102">&lt;kaldırma&gt; öğesi authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="74f14-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="74f14-103">Bir kimlik doğrulama modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="74f14-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="74f14-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="74f14-104">\<configuration></span></span>  
<span data-ttu-id="74f14-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="74f14-105">\<system.net></span></span>  
<span data-ttu-id="74f14-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="74f14-106">\<authenticationModules></span></span>  
<span data-ttu-id="74f14-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="74f14-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f14-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74f14-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74f14-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="74f14-109">Attributes and Elements</span></span>  
 <span data-ttu-id="74f14-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74f14-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74f14-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="74f14-111">Attributes</span></span>  
  
|<span data-ttu-id="74f14-112">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="74f14-112">**Attribute**</span></span>|<span data-ttu-id="74f14-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="74f14-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="74f14-114">**türü**</span><span class="sxs-lookup"><span data-stu-id="74f14-114">**type**</span></span>|<span data-ttu-id="74f14-115">Kaldırmak için kimlik doğrulama modülü adı.</span><span class="sxs-lookup"><span data-stu-id="74f14-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74f14-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="74f14-116">Child Elements</span></span>  
 <span data-ttu-id="74f14-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="74f14-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74f14-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="74f14-118">Parent Elements</span></span>  
  
|<span data-ttu-id="74f14-119">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="74f14-119">**Element**</span></span>|<span data-ttu-id="74f14-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="74f14-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="74f14-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="74f14-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="74f14-122">Ağ isteklerine kimlik doğrulaması için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="74f14-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74f14-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74f14-123">Remarks</span></span>  
 <span data-ttu-id="74f14-124">`remove` Öğeyi yapılandırma dosyası veya yapılandırma hiyerarşisindeki daha yüksek düzeyde daha önce tanımlanan kimlik doğrulama modülleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="74f14-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="74f14-125">Değeri `type` özniteliği geçerli bir sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74f14-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="74f14-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="74f14-126">Configuration Files</span></span>  
 <span data-ttu-id="74f14-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74f14-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74f14-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="74f14-128">Example</span></span>  
 <span data-ttu-id="74f14-129">Aşağıdaki örnek, bir kimlik doğrulama modülü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="74f14-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74f14-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74f14-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="74f14-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="74f14-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
