---
description: 'Daha fazla bilgi edinin: <clear> authenticationModules için öğesi (ağ ayarları)'
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
ms.openlocfilehash: ccfc9f53ef53268cdb1155673fc47a862a63419c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698576"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="18d05-103">authenticationModules için \<clear> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="18d05-103">\<clear> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="18d05-104">Tüm kimlik doğrulama modüllerini uygulamadan temizler.</span><span class="sxs-lookup"><span data-stu-id="18d05-104">Clears all authentication modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="18d05-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="18d05-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18d05-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="18d05-106">Attributes and Elements</span></span>  

 <span data-ttu-id="18d05-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18d05-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18d05-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="18d05-108">Attributes</span></span>  

 <span data-ttu-id="18d05-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="18d05-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="18d05-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="18d05-110">Child Elements</span></span>  

 <span data-ttu-id="18d05-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="18d05-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18d05-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="18d05-112">Parent Elements</span></span>  
  
|<span data-ttu-id="18d05-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="18d05-113">**Element**</span></span>|<span data-ttu-id="18d05-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="18d05-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="18d05-115">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="18d05-115">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="18d05-116">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="18d05-116">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18d05-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18d05-117">Remarks</span></span>  

 <span data-ttu-id="18d05-118">`clear`Öğesi, daha önce yapılandırma dosyasında veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan tüm kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="18d05-118">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="18d05-119">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="18d05-119">Configuration Files</span></span>  

 <span data-ttu-id="18d05-120">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="18d05-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18d05-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="18d05-121">Example</span></span>  

 <span data-ttu-id="18d05-122">Aşağıdaki örnek, tüm yapılandırılmış kimlik doğrulama modüllerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="18d05-122">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18d05-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18d05-123">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="18d05-124">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="18d05-124">Network Settings Schema</span></span>](index.md)
