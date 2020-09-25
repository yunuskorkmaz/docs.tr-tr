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
ms.openlocfilehash: 154a73a5fe3fa9e2b6b1c9e5c462b76bdc1ba640
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201752"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="87e86-102">\<authenticationModules> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="87e86-102">\<authenticationModules> Element (Network Settings)</span></span>

<span data-ttu-id="87e86-103">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="87e86-103">Specifies modules used to authenticate network requests.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a><span data-ttu-id="87e86-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="87e86-104">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87e86-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="87e86-105">Attributes and Elements</span></span>  

 <span data-ttu-id="87e86-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87e86-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87e86-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="87e86-107">Attributes</span></span>  

 <span data-ttu-id="87e86-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="87e86-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="87e86-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="87e86-109">Child Elements</span></span>  
  
|<span data-ttu-id="87e86-110">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="87e86-110">**Element**</span></span>|<span data-ttu-id="87e86-111">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="87e86-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="87e86-112">add</span><span class="sxs-lookup"><span data-stu-id="87e86-112">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="87e86-113">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="87e86-113">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="87e86-114">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="87e86-114">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="87e86-115">Tüm kimlik doğrulama modüllerini uygulamadan temizler.</span><span class="sxs-lookup"><span data-stu-id="87e86-115">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="87e86-116">temizlenmesine</span><span class="sxs-lookup"><span data-stu-id="87e86-116">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="87e86-117">Bir kimlik doğrulama modülünü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="87e86-117">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87e86-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="87e86-118">Parent Elements</span></span>  
  
|<span data-ttu-id="87e86-119">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="87e86-119">**Element**</span></span>|<span data-ttu-id="87e86-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="87e86-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="87e86-121">system.net</span><span class="sxs-lookup"><span data-stu-id="87e86-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="87e86-122">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="87e86-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87e86-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87e86-123">Remarks</span></span>  

 <span data-ttu-id="87e86-124">`authenticationModule`Öğesi, bir sunucusuyla kimlik doğrulama işlemini gerçekleştiren kimlik doğrulama modüllerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87e86-124">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="87e86-125">Bir kimlik doğrulama modülünün arabirimini uygulaması gerekir <xref:System.Net.IAuthenticationModule> .</span><span class="sxs-lookup"><span data-stu-id="87e86-125">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="87e86-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="87e86-126">Configuration Files</span></span>  

 <span data-ttu-id="87e86-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87e86-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87e86-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="87e86-128">Example</span></span>  

 <span data-ttu-id="87e86-129">Aşağıdaki örnek bir kimlik doğrulama modülünü mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="87e86-129">The following example enables an authentication module.</span></span> <span data-ttu-id="87e86-130">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="87e86-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="87e86-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87e86-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="87e86-132">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="87e86-132">Network Settings Schema</span></span>](index.md)
