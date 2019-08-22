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
ms.openlocfilehash: 12ac146926103b40073d34f48895b0645c8a8ed2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659475"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="43ee5-102">\<authenticationModules için > öğesini temizle (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="43ee5-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="43ee5-103">Tüm kimlik doğrulama modüllerini uygulamadan temizler.</span><span class="sxs-lookup"><span data-stu-id="43ee5-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="43ee5-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="43ee5-104">\<configuration></span></span>  
<span data-ttu-id="43ee5-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="43ee5-105">\<system.net></span></span>  
<span data-ttu-id="43ee5-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="43ee5-106">\<authenticationModules></span></span>  
<span data-ttu-id="43ee5-107">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="43ee5-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ee5-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43ee5-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43ee5-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43ee5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="43ee5-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43ee5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43ee5-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43ee5-111">Attributes</span></span>  
 <span data-ttu-id="43ee5-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="43ee5-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43ee5-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43ee5-113">Child Elements</span></span>  
 <span data-ttu-id="43ee5-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="43ee5-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43ee5-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43ee5-115">Parent Elements</span></span>  
  
|<span data-ttu-id="43ee5-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="43ee5-116">**Element**</span></span>|<span data-ttu-id="43ee5-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="43ee5-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="43ee5-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="43ee5-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="43ee5-119">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="43ee5-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43ee5-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43ee5-120">Remarks</span></span>  
 <span data-ttu-id="43ee5-121">Öğesi `clear` , daha önce yapılandırma dosyasında veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan tüm kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="43ee5-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="43ee5-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="43ee5-122">Configuration Files</span></span>  
 <span data-ttu-id="43ee5-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="43ee5-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43ee5-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="43ee5-124">Example</span></span>  
 <span data-ttu-id="43ee5-125">Aşağıdaki örnek, tüm yapılandırılmış kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="43ee5-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43ee5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43ee5-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="43ee5-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="43ee5-127">Network Settings Schema</span></span>](index.md)
