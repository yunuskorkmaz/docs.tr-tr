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
ms.openlocfilehash: 3c018c7d474286f7a9cde2d070e4b54d164b5b40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674616"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="120e9-102">\<Temizle > authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="120e9-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="120e9-103">Uygulamadaki tüm kimlik doğrulama modülleri temizler.</span><span class="sxs-lookup"><span data-stu-id="120e9-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="120e9-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="120e9-104">\<configuration></span></span>  
<span data-ttu-id="120e9-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="120e9-105">\<system.net></span></span>  
<span data-ttu-id="120e9-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="120e9-106">\<authenticationModules></span></span>  
<span data-ttu-id="120e9-107">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="120e9-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="120e9-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="120e9-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="120e9-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="120e9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="120e9-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="120e9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="120e9-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="120e9-111">Attributes</span></span>  
 <span data-ttu-id="120e9-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="120e9-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="120e9-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="120e9-113">Child Elements</span></span>  
 <span data-ttu-id="120e9-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="120e9-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="120e9-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="120e9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="120e9-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="120e9-116">**Element**</span></span>|<span data-ttu-id="120e9-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="120e9-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="120e9-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="120e9-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="120e9-119">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="120e9-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="120e9-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="120e9-120">Remarks</span></span>  
 <span data-ttu-id="120e9-121">`clear` Yapılandırma dosyasında ya da daha yüksek bir düzeyde yapılandırma hiyerarşideki daha önce tanımlanan tüm kimlik doğrulama modülü öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="120e9-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="120e9-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="120e9-122">Configuration Files</span></span>  
 <span data-ttu-id="120e9-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="120e9-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="120e9-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="120e9-124">Example</span></span>  
 <span data-ttu-id="120e9-125">Aşağıdaki örnek, tüm yapılandırılmış kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="120e9-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="120e9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="120e9-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="120e9-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="120e9-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
