---
title: authenticationModules için <remove> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: 0829f57d8dca91c2d895085dceaeea422229537c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176207"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="aa306-102">authenticationModules için \<remove> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="aa306-102">\<remove> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="aa306-103">Bir kimlik doğrulama modülünü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="aa306-103">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="aa306-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="aa306-104">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa306-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa306-105">Attributes and Elements</span></span>  

 <span data-ttu-id="aa306-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa306-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa306-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aa306-107">Attributes</span></span>  
  
|<span data-ttu-id="aa306-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="aa306-108">**Attribute**</span></span>|<span data-ttu-id="aa306-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="aa306-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="aa306-110">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="aa306-110">**type**</span></span>|<span data-ttu-id="aa306-111">Kaldırılacak kimlik doğrulama modülünün adı.</span><span class="sxs-lookup"><span data-stu-id="aa306-111">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa306-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa306-112">Child Elements</span></span>  

 <span data-ttu-id="aa306-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="aa306-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa306-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa306-114">Parent Elements</span></span>  
  
|<span data-ttu-id="aa306-115">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="aa306-115">**Element**</span></span>|<span data-ttu-id="aa306-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="aa306-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="aa306-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="aa306-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="aa306-118">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa306-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa306-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa306-119">Remarks</span></span>  

 <span data-ttu-id="aa306-120">`remove`Öğesi yapılandırma hiyerarşisinde daha önce tanımlanan kimlik doğrulama modüllerini veya yapılandırma hiyerarşisinde daha yüksek bir düzeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="aa306-120">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="aa306-121">`type`Özniteliğin değeri geçerli bir sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa306-121">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="aa306-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="aa306-122">Configuration Files</span></span>  

 <span data-ttu-id="aa306-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa306-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa306-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa306-124">Example</span></span>  

 <span data-ttu-id="aa306-125">Aşağıdaki örnek bir kimlik doğrulama modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="aa306-125">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa306-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa306-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="aa306-127">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="aa306-127">Network Settings Schema</span></span>](index.md)
