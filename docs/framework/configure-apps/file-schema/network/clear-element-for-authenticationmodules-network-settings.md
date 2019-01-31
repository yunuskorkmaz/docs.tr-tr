---
title: authenticationModules için <clear> Öğesi (Ağ Ayarları)
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
ms.openlocfilehash: d6760d05a8c2368cd20cae416b0b4b428b6588db
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279077"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="e461c-102">\<Temizle > authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="e461c-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="e461c-103">Uygulamadaki tüm kimlik doğrulama modülleri temizler.</span><span class="sxs-lookup"><span data-stu-id="e461c-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="e461c-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e461c-104">\<configuration></span></span>  
<span data-ttu-id="e461c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e461c-105">\<system.net></span></span>  
<span data-ttu-id="e461c-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="e461c-106">\<authenticationModules></span></span>  
<span data-ttu-id="e461c-107">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="e461c-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e461c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e461c-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e461c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e461c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e461c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e461c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e461c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e461c-111">Attributes</span></span>  
 <span data-ttu-id="e461c-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="e461c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e461c-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e461c-113">Child Elements</span></span>  
 <span data-ttu-id="e461c-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e461c-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e461c-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e461c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e461c-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="e461c-116">**Element**</span></span>|<span data-ttu-id="e461c-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e461c-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e461c-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="e461c-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="e461c-119">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e461c-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e461c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e461c-120">Remarks</span></span>  
 <span data-ttu-id="e461c-121">`clear` Yapılandırma dosyasında ya da daha yüksek bir düzeyde yapılandırma hiyerarşideki daha önce tanımlanan tüm kimlik doğrulama modülü öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e461c-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e461c-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e461c-122">Configuration Files</span></span>  
 <span data-ttu-id="e461c-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e461c-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e461c-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e461c-124">Example</span></span>  
 <span data-ttu-id="e461c-125">Aşağıdaki örnek, tüm yapılandırılmış kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e461c-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e461c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e461c-126">See also</span></span>
- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="e461c-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e461c-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
