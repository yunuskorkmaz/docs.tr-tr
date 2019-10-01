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
ms.openlocfilehash: 052f7eef30500d37389585956728250a46b718a3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698392"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="f9590-102">authenticationModules için \<clear > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="f9590-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="f9590-103">Tüm kimlik doğrulama modüllerini uygulamadan temizler.</span><span class="sxs-lookup"><span data-stu-id="f9590-103">Clears all authentication modules from the application.</span></span>  
  
[<span data-ttu-id="f9590-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="f9590-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="f9590-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f9590-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="f9590-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f9590-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="f9590-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="f9590-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9590-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9590-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9590-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9590-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f9590-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9590-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9590-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9590-111">Attributes</span></span>  
 <span data-ttu-id="f9590-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9590-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f9590-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9590-113">Child Elements</span></span>  
 <span data-ttu-id="f9590-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9590-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9590-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9590-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f9590-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="f9590-116">**Element**</span></span>|<span data-ttu-id="f9590-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f9590-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f9590-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="f9590-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="f9590-119">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9590-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9590-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9590-120">Remarks</span></span>  
 <span data-ttu-id="f9590-121">@No__t-0 öğesi, daha önce yapılandırma dosyasında veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan tüm kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f9590-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f9590-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f9590-122">Configuration Files</span></span>  
 <span data-ttu-id="f9590-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9590-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9590-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9590-124">Example</span></span>  
 <span data-ttu-id="f9590-125">Aşağıdaki örnek, tüm yapılandırılmış kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f9590-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9590-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9590-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="f9590-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f9590-127">Network Settings Schema</span></span>](index.md)
