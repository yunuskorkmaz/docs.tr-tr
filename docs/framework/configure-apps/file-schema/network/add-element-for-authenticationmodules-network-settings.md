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
ms.openlocfilehash: d72371921a85ff5a68dd9017f0fe8cf5d28557dd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664245"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="107a9-102">\<authenticationModules için > öğesi ekleme (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="107a9-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="107a9-103">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="107a9-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="107a9-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="107a9-104">\<configuration></span></span>  
<span data-ttu-id="107a9-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="107a9-105">\<system.net></span></span>  
<span data-ttu-id="107a9-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="107a9-106">\<authenticationModules></span></span>  
<span data-ttu-id="107a9-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="107a9-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107a9-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="107a9-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="107a9-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="107a9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="107a9-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="107a9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="107a9-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="107a9-111">Attributes</span></span>  
  
|<span data-ttu-id="107a9-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="107a9-112">**Attribute**</span></span>|<span data-ttu-id="107a9-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="107a9-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="107a9-114">Tam nitelikli tür adı ( <xref:System.Type.FullName%2A> özelliği ile gösterilir) ve derleme adı ( <xref:System.Reflection.Assembly.FullName%2A> özelliği ile gösterilir), virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="107a9-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="107a9-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="107a9-115">Child Elements</span></span>  
 <span data-ttu-id="107a9-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="107a9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="107a9-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="107a9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="107a9-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="107a9-118">**Element**</span></span>|<span data-ttu-id="107a9-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="107a9-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="107a9-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="107a9-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="107a9-121">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="107a9-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="107a9-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="107a9-122">Remarks</span></span>  
 <span data-ttu-id="107a9-123">`add` Öğesi, kayıtlı kimlik doğrulama modülleri listesinin sonuna bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="107a9-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="107a9-124">Kimlik doğrulama modülleri, listeye eklendikleri sırada çağırılır.</span><span class="sxs-lookup"><span data-stu-id="107a9-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="107a9-125">`type` Özniteliğin değeri, virgülle ayrılmış olarak geçerli bir tür adı ve karşılık gelen derleme adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="107a9-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="107a9-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="107a9-126">Configuration Files</span></span>  
 <span data-ttu-id="107a9-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="107a9-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="107a9-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="107a9-128">Example</span></span>  
 <span data-ttu-id="107a9-129">Aşağıdaki örnekte varsayılan kimlik doğrulama modülleri etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="107a9-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="107a9-130">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="107a9-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="107a9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="107a9-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="107a9-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="107a9-132">Network Settings Schema</span></span>](index.md)
