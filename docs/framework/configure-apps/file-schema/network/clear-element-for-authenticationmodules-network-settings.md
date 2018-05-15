---
title: '&lt;Clear&gt; öğesi authenticationModules (ağ ayarları) için'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 94e0242ca685e8b0118a55ba44fb0569c13f10f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="9eeba-102">&lt;Clear&gt; öğesi authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="9eeba-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="9eeba-103">Uygulamadaki tüm kimlik doğrulama modülleri temizler.</span><span class="sxs-lookup"><span data-stu-id="9eeba-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="9eeba-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="9eeba-104">\<configuration></span></span>  
<span data-ttu-id="9eeba-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="9eeba-105">\<system.net></span></span>  
<span data-ttu-id="9eeba-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="9eeba-106">\<authenticationModules></span></span>  
<span data-ttu-id="9eeba-107">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="9eeba-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eeba-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9eeba-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eeba-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9eeba-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9eeba-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9eeba-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eeba-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9eeba-111">Attributes</span></span>  
 <span data-ttu-id="9eeba-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="9eeba-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9eeba-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9eeba-113">Child Elements</span></span>  
 <span data-ttu-id="9eeba-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="9eeba-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9eeba-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9eeba-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9eeba-116">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="9eeba-116">**Element**</span></span>|<span data-ttu-id="9eeba-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="9eeba-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9eeba-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="9eeba-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="9eeba-119">Ağ isteklerine kimlik doğrulaması için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="9eeba-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eeba-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9eeba-120">Remarks</span></span>  
 <span data-ttu-id="9eeba-121">`clear` Öğeyi yapılandırma dosyası veya yapılandırma hiyerarşisindeki daha yüksek düzeyde daha önce tanımlanan tüm kimlik doğrulama modülleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9eeba-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9eeba-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="9eeba-122">Configuration Files</span></span>  
 <span data-ttu-id="9eeba-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9eeba-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eeba-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="9eeba-124">Example</span></span>  
 <span data-ttu-id="9eeba-125">Aşağıdaki örnek, tüm yapılandırılmış kimlik doğrulaması modülleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9eeba-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9eeba-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9eeba-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="9eeba-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="9eeba-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
