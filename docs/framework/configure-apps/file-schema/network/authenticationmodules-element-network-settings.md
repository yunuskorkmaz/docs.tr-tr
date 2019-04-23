---
title: <authenticationModules> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 8878bcbdf8b3613677231db3e91a6d71dfa10bae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143344"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="038d1-102">\<authenticationModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="038d1-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="038d1-103">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="038d1-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="038d1-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="038d1-104">\<configuration></span></span>  
<span data-ttu-id="038d1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="038d1-105">\<system.net></span></span>  
<span data-ttu-id="038d1-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="038d1-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="038d1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="038d1-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="038d1-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="038d1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="038d1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="038d1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="038d1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="038d1-110">Attributes</span></span>  
 <span data-ttu-id="038d1-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="038d1-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="038d1-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="038d1-112">Child Elements</span></span>  
  
|<span data-ttu-id="038d1-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="038d1-113">**Element**</span></span>|<span data-ttu-id="038d1-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="038d1-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="038d1-115">add</span><span class="sxs-lookup"><span data-stu-id="038d1-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="038d1-116">Uygulamasına bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="038d1-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="038d1-117">Temizle</span><span class="sxs-lookup"><span data-stu-id="038d1-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="038d1-118">Uygulamadaki tüm kimlik doğrulama modülleri temizler.</span><span class="sxs-lookup"><span data-stu-id="038d1-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="038d1-119">remove</span><span class="sxs-lookup"><span data-stu-id="038d1-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="038d1-120">Bir kimlik doğrulama modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="038d1-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="038d1-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="038d1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="038d1-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="038d1-122">**Element**</span></span>|<span data-ttu-id="038d1-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="038d1-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="038d1-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="038d1-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="038d1-125">.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="038d1-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="038d1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="038d1-126">Remarks</span></span>  
 <span data-ttu-id="038d1-127">`authenticationModule` Öğesi ile bir sunucu kimlik doğrulama işlemi gerçekleştir kimlik doğrulama modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="038d1-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="038d1-128">Bir kimlik doğrulama modülü uygulamalıdır <xref:System.Net.IAuthenticationModule> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="038d1-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="038d1-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="038d1-129">Configuration Files</span></span>  
 <span data-ttu-id="038d1-130">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="038d1-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="038d1-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="038d1-131">Example</span></span>  
 <span data-ttu-id="038d1-132">Aşağıdaki örnek, bir kimlik doğrulama modülü sağlar.</span><span class="sxs-lookup"><span data-stu-id="038d1-132">The following example enables an authentication module.</span></span> <span data-ttu-id="038d1-133">Belirtilen modül için doğru değerlerle PublicKeyToken ve Version değerleri değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="038d1-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="038d1-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="038d1-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="038d1-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="038d1-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
