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
ms.openlocfilehash: 9c011cf1216b98fa20e330e185e4cf2c331b31d4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087947"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="c5887-102">authenticationModules için > öğesi eklemek \<(ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="c5887-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="c5887-103">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="c5887-103">Adds an authentication module to the application.</span></span>  

<span data-ttu-id="c5887-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c5887-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c5887-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="c5887-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="c5887-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c5887-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="c5887-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**</span><span class="sxs-lookup"><span data-stu-id="c5887-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c5887-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5887-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5887-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5887-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c5887-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5887-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5887-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5887-111">Attributes</span></span>  
  
|<span data-ttu-id="c5887-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="c5887-112">**Attribute**</span></span>|<span data-ttu-id="c5887-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c5887-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="c5887-114">Tam nitelikli tür adı (<xref:System.Type.FullName%2A> özelliği ile gösterilir) ve derleme adı (<xref:System.Reflection.Assembly.FullName%2A> özelliği tarafından belirtilir), virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c5887-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5887-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5887-115">Child Elements</span></span>  
 <span data-ttu-id="c5887-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5887-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5887-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5887-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c5887-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="c5887-118">**Element**</span></span>|<span data-ttu-id="c5887-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c5887-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c5887-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="c5887-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="c5887-121">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5887-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5887-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5887-122">Remarks</span></span>  
 <span data-ttu-id="c5887-123">`add` öğesi, kayıtlı kimlik doğrulama modülleri listesinin sonuna bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="c5887-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="c5887-124">Kimlik doğrulama modülleri, listeye eklendikleri sırada çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c5887-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="c5887-125">`type` özniteliğin değeri, virgülle ayrılmış olarak geçerli bir tür adı ve karşılık gelen derleme adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5887-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c5887-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="c5887-126">Configuration Files</span></span>  
 <span data-ttu-id="c5887-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5887-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5887-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5887-128">Example</span></span>  
 <span data-ttu-id="c5887-129">Aşağıdaki örnekte varsayılan kimlik doğrulama modülleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c5887-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="c5887-130">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c5887-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5887-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5887-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="c5887-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c5887-132">Network Settings Schema</span></span>](index.md)
