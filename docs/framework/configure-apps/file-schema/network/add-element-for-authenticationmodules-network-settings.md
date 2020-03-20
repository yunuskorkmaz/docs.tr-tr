---
title: authenticationModules için <add> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
ms.openlocfilehash: 4181a045079bdb455a63ebda722dd6b0daf33c4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155121"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="93a50-102">\<kimlik doğrulama modülleri için> Öğesi ekleModüller (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="93a50-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="93a50-103">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="93a50-103">Adds an authentication module to the application.</span></span>  

<span data-ttu-id="93a50-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="93a50-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93a50-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="93a50-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="93a50-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kimlik doğrulamaModülleri>**](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="93a50-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="93a50-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="93a50-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="93a50-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93a50-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93a50-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="93a50-109">Attributes and Elements</span></span>  
 <span data-ttu-id="93a50-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93a50-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93a50-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="93a50-111">Attributes</span></span>  
  
|<span data-ttu-id="93a50-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="93a50-112">**Attribute**</span></span>|<span data-ttu-id="93a50-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="93a50-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="93a50-114">Tam nitelikli tür adı <xref:System.Type.FullName%2A> (özellik tarafından gösterilir) ve montaj <xref:System.Reflection.Assembly.FullName%2A> adı (özellik tarafından gösterilir), bir virgül ile ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="93a50-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93a50-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="93a50-115">Child Elements</span></span>  
 <span data-ttu-id="93a50-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="93a50-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93a50-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="93a50-117">Parent Elements</span></span>  
  
|<span data-ttu-id="93a50-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="93a50-118">**Element**</span></span>|<span data-ttu-id="93a50-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="93a50-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="93a50-120">kimlik doğrulamaModülleri</span><span class="sxs-lookup"><span data-stu-id="93a50-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="93a50-121">Ağ isteklerini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="93a50-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93a50-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93a50-122">Remarks</span></span>  
 <span data-ttu-id="93a50-123">Öğe, `add` kayıtlı kimlik doğrulama modülleri listesinin sonuna bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="93a50-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="93a50-124">Kimlik doğrulama modülleri, listeye eklendikleri sırada çağrılır.</span><span class="sxs-lookup"><span data-stu-id="93a50-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="93a50-125">Öznitelik için `type` değer geçerli bir tür adı ve ilgili derleme adı, bir virgül ile ayrılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="93a50-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="93a50-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="93a50-126">Configuration Files</span></span>  
 <span data-ttu-id="93a50-127">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="93a50-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93a50-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="93a50-128">Example</span></span>  
 <span data-ttu-id="93a50-129">Aşağıdaki örnekte varsayılan kimlik doğrulama modülleri etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="93a50-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="93a50-130">Sürüm ve PublicKeyToken değerlerini belirtilen modül için doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="93a50-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93a50-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93a50-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="93a50-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="93a50-132">Network Settings Schema</span></span>](index.md)
