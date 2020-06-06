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
ms.openlocfilehash: e3abd1b4c76ebda885703ccf961d58657b582f19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087508"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="ff4aa-102">authenticationModules için \<clear> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="ff4aa-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="ff4aa-103">Tüm kimlik doğrulama modüllerini uygulamadan temizler.</span><span class="sxs-lookup"><span data-stu-id="ff4aa-103">Clears all authentication modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="ff4aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff4aa-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff4aa-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff4aa-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ff4aa-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff4aa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff4aa-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ff4aa-107">Attributes</span></span>  
 <span data-ttu-id="ff4aa-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="ff4aa-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ff4aa-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff4aa-109">Child Elements</span></span>  
 <span data-ttu-id="ff4aa-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="ff4aa-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff4aa-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff4aa-111">Parent Elements</span></span>  
  
|<span data-ttu-id="ff4aa-112">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="ff4aa-112">**Element**</span></span>|<span data-ttu-id="ff4aa-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="ff4aa-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ff4aa-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="ff4aa-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="ff4aa-115">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff4aa-115">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff4aa-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff4aa-116">Remarks</span></span>  
 <span data-ttu-id="ff4aa-117">`clear`Öğesi, daha önce yapılandırma dosyasında veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan tüm kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ff4aa-117">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ff4aa-118">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="ff4aa-118">Configuration Files</span></span>  
 <span data-ttu-id="ff4aa-119">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff4aa-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff4aa-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff4aa-120">Example</span></span>  
 <span data-ttu-id="ff4aa-121">Aşağıdaki örnek, tüm yapılandırılmış kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ff4aa-121">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff4aa-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff4aa-122">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="ff4aa-123">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ff4aa-123">Network Settings Schema</span></span>](index.md)
