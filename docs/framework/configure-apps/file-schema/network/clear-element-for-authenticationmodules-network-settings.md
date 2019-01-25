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
ms.openlocfilehash: b2f5194cc6a4c7c0329edb2a1718a642781f79b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563424"
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="5fbd8-102">&lt;Temizle&gt; authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="5fbd8-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="5fbd8-103">Uygulamadaki tüm kimlik doğrulama modülleri temizler.</span><span class="sxs-lookup"><span data-stu-id="5fbd8-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="5fbd8-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5fbd8-104">\<configuration></span></span>  
<span data-ttu-id="5fbd8-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5fbd8-105">\<system.net></span></span>  
<span data-ttu-id="5fbd8-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="5fbd8-106">\<authenticationModules></span></span>  
<span data-ttu-id="5fbd8-107">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="5fbd8-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fbd8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fbd8-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fbd8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fbd8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5fbd8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fbd8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fbd8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5fbd8-111">Attributes</span></span>  
 <span data-ttu-id="5fbd8-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="5fbd8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5fbd8-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fbd8-113">Child Elements</span></span>  
 <span data-ttu-id="5fbd8-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="5fbd8-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fbd8-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fbd8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5fbd8-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5fbd8-116">**Element**</span></span>|<span data-ttu-id="5fbd8-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5fbd8-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5fbd8-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="5fbd8-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="5fbd8-119">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fbd8-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fbd8-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fbd8-120">Remarks</span></span>  
 <span data-ttu-id="5fbd8-121">`clear` Yapılandırma dosyasında ya da daha yüksek bir düzeyde yapılandırma hiyerarşideki daha önce tanımlanan tüm kimlik doğrulama modülü öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5fbd8-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5fbd8-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5fbd8-122">Configuration Files</span></span>  
 <span data-ttu-id="5fbd8-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fbd8-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fbd8-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fbd8-124">Example</span></span>  
 <span data-ttu-id="5fbd8-125">Aşağıdaki örnek, tüm yapılandırılmış kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5fbd8-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fbd8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fbd8-126">See also</span></span>
- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="5fbd8-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5fbd8-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
