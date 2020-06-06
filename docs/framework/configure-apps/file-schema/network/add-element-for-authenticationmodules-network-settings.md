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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155121"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="76108-102">authenticationModules için \<add> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="76108-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="76108-103">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="76108-103">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="76108-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76108-104">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76108-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="76108-105">Attributes and Elements</span></span>  
 <span data-ttu-id="76108-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="76108-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76108-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="76108-107">Attributes</span></span>  
  
|<span data-ttu-id="76108-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="76108-108">**Attribute**</span></span>|<span data-ttu-id="76108-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="76108-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="76108-110">Tam nitelikli tür adı (özelliği ile gösterilir <xref:System.Type.FullName%2A> ) ve derleme adı (özelliği ile gösterilir <xref:System.Reflection.Assembly.FullName%2A> ), virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="76108-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76108-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="76108-111">Child Elements</span></span>  
 <span data-ttu-id="76108-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="76108-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76108-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="76108-113">Parent Elements</span></span>  
  
|<span data-ttu-id="76108-114">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="76108-114">**Element**</span></span>|<span data-ttu-id="76108-115">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="76108-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="76108-116">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="76108-116">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="76108-117">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="76108-117">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76108-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76108-118">Remarks</span></span>  
 <span data-ttu-id="76108-119">`add`Öğesi, kayıtlı kimlik doğrulama modülleri listesinin sonuna bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="76108-119">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="76108-120">Kimlik doğrulama modülleri, listeye eklendikleri sırada çağırılır.</span><span class="sxs-lookup"><span data-stu-id="76108-120">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="76108-121">Özniteliğin değeri, `type` virgülle ayrılmış olarak geçerli bir tür adı ve karşılık gelen derleme adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76108-121">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="76108-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="76108-122">Configuration Files</span></span>  
 <span data-ttu-id="76108-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76108-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76108-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="76108-124">Example</span></span>  
 <span data-ttu-id="76108-125">Aşağıdaki örnekte varsayılan kimlik doğrulama modülleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="76108-125">The following example enables the default authentication modules.</span></span> <span data-ttu-id="76108-126">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="76108-126">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76108-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76108-127">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="76108-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="76108-128">Network Settings Schema</span></span>](index.md)
