---
title: '&lt;authenticationModules&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6d7f811a5746fa07264a192efdc4c5c02323e1f4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltauthenticationmodulesgt-element-network-settings"></a><span data-ttu-id="3794c-102">&lt;authenticationModules&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3794c-102">&lt;authenticationModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="3794c-103">Ağ isteklerine kimlik doğrulaması için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3794c-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="3794c-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3794c-104">\<configuration></span></span>  
<span data-ttu-id="3794c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3794c-105">\<system.net></span></span>  
<span data-ttu-id="3794c-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="3794c-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3794c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3794c-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3794c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3794c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3794c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3794c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3794c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3794c-110">Attributes</span></span>  
 <span data-ttu-id="3794c-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="3794c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3794c-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3794c-112">Child Elements</span></span>  
  
|<span data-ttu-id="3794c-113">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="3794c-113">**Element**</span></span>|<span data-ttu-id="3794c-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="3794c-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3794c-115">add</span><span class="sxs-lookup"><span data-stu-id="3794c-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="3794c-116">Bir kimlik doğrulama modülü uygulamaya ekler.</span><span class="sxs-lookup"><span data-stu-id="3794c-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="3794c-117">Temizle</span><span class="sxs-lookup"><span data-stu-id="3794c-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="3794c-118">Uygulamadaki tüm kimlik doğrulama modülleri temizler.</span><span class="sxs-lookup"><span data-stu-id="3794c-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="3794c-119">remove</span><span class="sxs-lookup"><span data-stu-id="3794c-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="3794c-120">Bir kimlik doğrulama modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3794c-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3794c-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3794c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3794c-122">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="3794c-122">**Element**</span></span>|<span data-ttu-id="3794c-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="3794c-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3794c-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="3794c-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="3794c-125">.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="3794c-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3794c-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3794c-126">Remarks</span></span>  
 <span data-ttu-id="3794c-127">`authenticationModule` Öğesi ile bir sunucu kimlik doğrulama işlemi gerçekleştir kimlik doğrulama modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3794c-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="3794c-128">Bir kimlik doğrulama modülü uygulamalıdır <xref:System.Net.IAuthenticationModule> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3794c-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3794c-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="3794c-129">Configuration Files</span></span>  
 <span data-ttu-id="3794c-130">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3794c-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3794c-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="3794c-131">Example</span></span>  
 <span data-ttu-id="3794c-132">Aşağıdaki örnek, bir kimlik doğrulama modülü sağlar.</span><span class="sxs-lookup"><span data-stu-id="3794c-132">The following example enables an authentication module.</span></span> <span data-ttu-id="3794c-133">Belirtilen modül için doğru değerlerle sürüm ve PublicKeyToken için değerleri değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3794c-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3794c-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3794c-134">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="3794c-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3794c-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
