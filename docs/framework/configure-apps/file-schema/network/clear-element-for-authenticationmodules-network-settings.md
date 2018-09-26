---
title: '&lt;Temizle&gt; authenticationModules (ağ ayarları) için'
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
ms.openlocfilehash: ef12a475dde103023d3411fb68efb3bdb4f6d116
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47076699"
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="4730e-102">&lt;Temizle&gt; authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="4730e-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="4730e-103">Uygulamadaki tüm kimlik doğrulama modülleri temizler.</span><span class="sxs-lookup"><span data-stu-id="4730e-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="4730e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="4730e-104">\<configuration></span></span>  
<span data-ttu-id="4730e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4730e-105">\<system.net></span></span>  
<span data-ttu-id="4730e-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="4730e-106">\<authenticationModules></span></span>  
<span data-ttu-id="4730e-107">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="4730e-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4730e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4730e-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4730e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4730e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4730e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4730e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4730e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4730e-111">Attributes</span></span>  
 <span data-ttu-id="4730e-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="4730e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4730e-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4730e-113">Child Elements</span></span>  
 <span data-ttu-id="4730e-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="4730e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4730e-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4730e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4730e-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="4730e-116">**Element**</span></span>|<span data-ttu-id="4730e-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="4730e-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4730e-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="4730e-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="4730e-119">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4730e-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4730e-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4730e-120">Remarks</span></span>  
 <span data-ttu-id="4730e-121">`clear` Yapılandırma dosyasında ya da daha yüksek bir düzeyde yapılandırma hiyerarşideki daha önce tanımlanan tüm kimlik doğrulama modülü öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4730e-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4730e-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4730e-122">Configuration Files</span></span>  
 <span data-ttu-id="4730e-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4730e-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4730e-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="4730e-124">Example</span></span>  
 <span data-ttu-id="4730e-125">Aşağıdaki örnek, tüm yapılandırılmış kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4730e-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4730e-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4730e-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="4730e-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4730e-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
