---
description: 'Daha fazla bilgi edinin: <authenticationModules> öğesi (ağ ayarları)'
title: <authenticationModules> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 2c2dc3c6a3d8fc064bb24c3d86a4441c269e43f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698628"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="0da66-103">\<authenticationModules> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="0da66-103">\<authenticationModules> Element (Network Settings)</span></span>

<span data-ttu-id="0da66-104">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="0da66-104">Specifies modules used to authenticate network requests.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a><span data-ttu-id="0da66-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0da66-105">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0da66-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0da66-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0da66-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0da66-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0da66-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0da66-108">Attributes</span></span>  

 <span data-ttu-id="0da66-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="0da66-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0da66-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0da66-110">Child Elements</span></span>  
  
|<span data-ttu-id="0da66-111">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="0da66-111">**Element**</span></span>|<span data-ttu-id="0da66-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0da66-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0da66-113">add</span><span class="sxs-lookup"><span data-stu-id="0da66-113">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="0da66-114">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="0da66-114">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="0da66-115">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="0da66-115">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="0da66-116">Tüm kimlik doğrulama modüllerini uygulamadan temizler.</span><span class="sxs-lookup"><span data-stu-id="0da66-116">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="0da66-117">temizlenmesine</span><span class="sxs-lookup"><span data-stu-id="0da66-117">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="0da66-118">Bir kimlik doğrulama modülünü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0da66-118">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0da66-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0da66-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0da66-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="0da66-120">**Element**</span></span>|<span data-ttu-id="0da66-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0da66-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0da66-122">system.net</span><span class="sxs-lookup"><span data-stu-id="0da66-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="0da66-123">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="0da66-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0da66-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0da66-124">Remarks</span></span>  

 <span data-ttu-id="0da66-125">`authenticationModule`Öğesi, bir sunucusuyla kimlik doğrulama işlemini gerçekleştiren kimlik doğrulama modüllerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0da66-125">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="0da66-126">Bir kimlik doğrulama modülünün arabirimini uygulaması gerekir <xref:System.Net.IAuthenticationModule> .</span><span class="sxs-lookup"><span data-stu-id="0da66-126">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0da66-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="0da66-127">Configuration Files</span></span>  

 <span data-ttu-id="0da66-128">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0da66-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0da66-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="0da66-129">Example</span></span>  

 <span data-ttu-id="0da66-130">Aşağıdaki örnek bir kimlik doğrulama modülünü mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="0da66-130">The following example enables an authentication module.</span></span> <span data-ttu-id="0da66-131">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="0da66-131">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0da66-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0da66-132">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="0da66-133">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="0da66-133">Network Settings Schema</span></span>](index.md)
