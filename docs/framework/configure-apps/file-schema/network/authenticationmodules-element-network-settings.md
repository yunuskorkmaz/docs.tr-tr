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
ms.openlocfilehash: 6488bfcd97e27a184b4a8cd1498d1c60f32babda
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659479"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="5b603-102">\<authenticationModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="5b603-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="5b603-103">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b603-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="5b603-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5b603-104">\<configuration></span></span>  
<span data-ttu-id="5b603-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5b603-105">\<system.net></span></span>  
<span data-ttu-id="5b603-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="5b603-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b603-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b603-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b603-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b603-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5b603-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b603-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b603-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5b603-110">Attributes</span></span>  
 <span data-ttu-id="5b603-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="5b603-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b603-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b603-112">Child Elements</span></span>  
  
|<span data-ttu-id="5b603-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5b603-113">**Element**</span></span>|<span data-ttu-id="5b603-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5b603-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5b603-115">add</span><span class="sxs-lookup"><span data-stu-id="5b603-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="5b603-116">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="5b603-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="5b603-117">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="5b603-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="5b603-118">Tüm kimlik doğrulama modüllerini uygulamadan temizler.</span><span class="sxs-lookup"><span data-stu-id="5b603-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="5b603-119">remove</span><span class="sxs-lookup"><span data-stu-id="5b603-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="5b603-120">Bir kimlik doğrulama modülünü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5b603-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b603-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b603-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5b603-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5b603-122">**Element**</span></span>|<span data-ttu-id="5b603-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5b603-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5b603-124">system.net</span><span class="sxs-lookup"><span data-stu-id="5b603-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="5b603-125">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="5b603-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b603-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b603-126">Remarks</span></span>  
 <span data-ttu-id="5b603-127">`authenticationModule` Öğesi, bir sunucusuyla kimlik doğrulama işlemini gerçekleştiren kimlik doğrulama modüllerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b603-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="5b603-128">Bir kimlik doğrulama modülünün <xref:System.Net.IAuthenticationModule> arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b603-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5b603-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5b603-129">Configuration Files</span></span>  
 <span data-ttu-id="5b603-130">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b603-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b603-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b603-131">Example</span></span>  
 <span data-ttu-id="5b603-132">Aşağıdaki örnek bir kimlik doğrulama modülünü mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="5b603-132">The following example enables an authentication module.</span></span> <span data-ttu-id="5b603-133">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5b603-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b603-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b603-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="5b603-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5b603-135">Network Settings Schema</span></span>](index.md)
