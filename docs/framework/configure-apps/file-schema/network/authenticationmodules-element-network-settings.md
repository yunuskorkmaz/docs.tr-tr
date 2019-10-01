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
ms.openlocfilehash: 4fe44deba951e5302518ed855589ad1b0ca75343
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699528"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="73433-102">\<authenticationModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="73433-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="73433-103">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="73433-103">Specifies modules used to authenticate network requests.</span></span>  
  
[<span data-ttu-id="73433-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="73433-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="73433-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="73433-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="73433-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<authenticationModules >**</span><span class="sxs-lookup"><span data-stu-id="73433-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73433-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73433-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73433-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73433-108">Attributes and Elements</span></span>  
 <span data-ttu-id="73433-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73433-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73433-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73433-110">Attributes</span></span>  
 <span data-ttu-id="73433-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="73433-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73433-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73433-112">Child Elements</span></span>  
  
|<span data-ttu-id="73433-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="73433-113">**Element**</span></span>|<span data-ttu-id="73433-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="73433-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="73433-115">add</span><span class="sxs-lookup"><span data-stu-id="73433-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="73433-116">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="73433-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="73433-117">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="73433-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="73433-118">Tüm kimlik doğrulama modüllerini uygulamadan temizler.</span><span class="sxs-lookup"><span data-stu-id="73433-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="73433-119">remove</span><span class="sxs-lookup"><span data-stu-id="73433-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="73433-120">Bir kimlik doğrulama modülünü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="73433-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73433-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73433-121">Parent Elements</span></span>  
  
|<span data-ttu-id="73433-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="73433-122">**Element**</span></span>|<span data-ttu-id="73433-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="73433-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="73433-124">system.net</span><span class="sxs-lookup"><span data-stu-id="73433-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="73433-125">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="73433-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73433-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73433-126">Remarks</span></span>  
 <span data-ttu-id="73433-127">@No__t-0 öğesi, bir sunucusuyla kimlik doğrulama işlemini gerçekleştiren kimlik doğrulama modüllerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73433-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="73433-128">Bir kimlik doğrulama modülünün <xref:System.Net.IAuthenticationModule> arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73433-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="73433-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="73433-129">Configuration Files</span></span>  
 <span data-ttu-id="73433-130">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73433-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73433-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="73433-131">Example</span></span>  
 <span data-ttu-id="73433-132">Aşağıdaki örnek bir kimlik doğrulama modülünü mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="73433-132">The following example enables an authentication module.</span></span> <span data-ttu-id="73433-133">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="73433-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73433-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73433-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="73433-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="73433-135">Network Settings Schema</span></span>](index.md)
