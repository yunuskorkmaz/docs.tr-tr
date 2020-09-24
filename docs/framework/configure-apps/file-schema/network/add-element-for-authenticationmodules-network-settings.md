---
title: authenticationModules için <add> Öğesi (Ağ Ayarları)
description: <add>ConnectionManagement için ağ ayarları öğesi .NET Framework bağlantı yönetimi listesine BIR IP adresi veya DNS adı ekler.
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
ms.openlocfilehash: f679a43ed1851e9681a2a57ca1639f8aa75aa8b3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149510"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="9ecb3-103">authenticationModules için \<add> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="9ecb3-103">\<add> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="9ecb3-104">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-104">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="9ecb3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ecb3-105">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ecb3-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ecb3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9ecb3-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ecb3-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9ecb3-108">Attributes</span></span>  
  
|<span data-ttu-id="9ecb3-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="9ecb3-109">**Attribute**</span></span>|<span data-ttu-id="9ecb3-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="9ecb3-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="9ecb3-111">Tam nitelikli tür adı (özelliği ile gösterilir <xref:System.Type.FullName%2A> ) ve derleme adı (özelliği ile gösterilir <xref:System.Reflection.Assembly.FullName%2A> ), virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ecb3-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ecb3-112">Child Elements</span></span>  

 <span data-ttu-id="9ecb3-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ecb3-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ecb3-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9ecb3-115">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="9ecb3-115">**Element**</span></span>|<span data-ttu-id="9ecb3-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="9ecb3-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9ecb3-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="9ecb3-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="9ecb3-118">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ecb3-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ecb3-119">Remarks</span></span>  

 <span data-ttu-id="9ecb3-120">`add`Öğesi, kayıtlı kimlik doğrulama modülleri listesinin sonuna bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-120">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="9ecb3-121">Kimlik doğrulama modülleri, listeye eklendikleri sırada çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-121">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="9ecb3-122">Özniteliğin değeri, `type` virgülle ayrılmış olarak geçerli bir tür adı ve karşılık gelen derleme adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-122">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9ecb3-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="9ecb3-123">Configuration Files</span></span>  

 <span data-ttu-id="9ecb3-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ecb3-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ecb3-125">Example</span></span>  

 <span data-ttu-id="9ecb3-126">Aşağıdaki örnekte varsayılan kimlik doğrulama modülleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-126">The following example enables the default authentication modules.</span></span> <span data-ttu-id="9ecb3-127">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-127">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ecb3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ecb3-128">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="9ecb3-129">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="9ecb3-129">Network Settings Schema</span></span>](index.md)
