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
ms.openlocfilehash: a68434aaa118db60a502c2bcc0bb188b83b0f463
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698427"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="c1954-102">\<authenticationmodules için > öğesi ekleme (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="c1954-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="c1954-103">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="c1954-103">Adds an authentication module to the application.</span></span>  
  
[<span data-ttu-id="c1954-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="c1954-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c1954-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c1954-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="c1954-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c1954-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="c1954-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**</span><span class="sxs-lookup"><span data-stu-id="c1954-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1954-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1954-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1954-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1954-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c1954-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1954-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1954-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1954-111">Attributes</span></span>  
  
|<span data-ttu-id="c1954-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="c1954-112">**Attribute**</span></span>|<span data-ttu-id="c1954-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c1954-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="c1954-114">Tam nitelikli tür adı (<xref:System.Type.FullName%2A> özelliği ile gösterilir) ve derleme adı (<xref:System.Reflection.Assembly.FullName%2A> özelliği ile belirtilir), virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c1954-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1954-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1954-115">Child Elements</span></span>  
 <span data-ttu-id="c1954-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1954-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1954-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1954-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c1954-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="c1954-118">**Element**</span></span>|<span data-ttu-id="c1954-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c1954-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c1954-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="c1954-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="c1954-121">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1954-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1954-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1954-122">Remarks</span></span>  
 <span data-ttu-id="c1954-123">@No__t-0 öğesi, kayıtlı kimlik doğrulama modülleri listesinin sonuna bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="c1954-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="c1954-124">Kimlik doğrulama modülleri, listeye eklendikleri sırada çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c1954-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="c1954-125">@No__t-0 özniteliğinin değeri, virgülle ayrılmış geçerli bir tür adı ve karşılık gelen derleme adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c1954-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c1954-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="c1954-126">Configuration Files</span></span>  
 <span data-ttu-id="c1954-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1954-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1954-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1954-128">Example</span></span>  
 <span data-ttu-id="c1954-129">Aşağıdaki örnekte varsayılan kimlik doğrulama modülleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c1954-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="c1954-130">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c1954-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1954-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1954-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="c1954-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c1954-132">Network Settings Schema</span></span>](index.md)
