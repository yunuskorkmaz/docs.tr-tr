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
ms.openlocfilehash: 12dc8be762e1158ddaabbd67e7165d7bdaca6461
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276334"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="acf34-102">\<Ekle > authenticationModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="acf34-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="acf34-103">Uygulamasına bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="acf34-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="acf34-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="acf34-104">\<configuration></span></span>  
<span data-ttu-id="acf34-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="acf34-105">\<system.net></span></span>  
<span data-ttu-id="acf34-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="acf34-106">\<authenticationModules></span></span>  
<span data-ttu-id="acf34-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="acf34-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf34-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acf34-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acf34-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="acf34-109">Attributes and Elements</span></span>  
 <span data-ttu-id="acf34-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="acf34-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acf34-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="acf34-111">Attributes</span></span>  
  
|<span data-ttu-id="acf34-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="acf34-112">**Attribute**</span></span>|<span data-ttu-id="acf34-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="acf34-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="acf34-114">Tam nitelikli tür adı (belirttiği <xref:System.Type.FullName%2A> özelliği) ve derleme adı (belirttiği <xref:System.Reflection.Assembly.FullName%2A> özelliği) virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="acf34-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="acf34-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="acf34-115">Child Elements</span></span>  
 <span data-ttu-id="acf34-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="acf34-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="acf34-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="acf34-117">Parent Elements</span></span>  
  
|<span data-ttu-id="acf34-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="acf34-118">**Element**</span></span>|<span data-ttu-id="acf34-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="acf34-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="acf34-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="acf34-120">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="acf34-121">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="acf34-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acf34-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acf34-122">Remarks</span></span>  
 <span data-ttu-id="acf34-123">`add` Öğesi bir kimlik doğrulama modülü kayıtlı kimlik doğrulama modülleri listesinin sonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="acf34-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="acf34-124">Kimlik doğrulama modülleri listeye eklendikleri sırayla çağrılır.</span><span class="sxs-lookup"><span data-stu-id="acf34-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="acf34-125">Değeri `type` özniteliği geçerli tür adı ve karşılık gelen derleme adı, virgülle ayrılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="acf34-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="acf34-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="acf34-126">Configuration Files</span></span>  
 <span data-ttu-id="acf34-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acf34-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="acf34-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="acf34-128">Example</span></span>  
 <span data-ttu-id="acf34-129">Aşağıdaki örnek, varsayılan kimlik doğrulama modülü sağlar.</span><span class="sxs-lookup"><span data-stu-id="acf34-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="acf34-130">Belirtilen modül için doğru değerlerle PublicKeyToken ve Version değerleri değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="acf34-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="acf34-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acf34-131">See also</span></span>
- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="acf34-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="acf34-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
