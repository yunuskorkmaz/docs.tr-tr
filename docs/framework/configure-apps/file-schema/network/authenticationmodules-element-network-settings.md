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
ms.openlocfilehash: bacaaf92464a355804a9ea8307f6e6f1caac1f05
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087607"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="24647-102">\<authenticationModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="24647-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="24647-103">Ağ isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="24647-103">Specifies modules used to authenticate network requests.</span></span>  

<span data-ttu-id="24647-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="24647-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="24647-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="24647-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="24647-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<authenticationModules >**</span><span class="sxs-lookup"><span data-stu-id="24647-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>

## <a name="syntax"></a><span data-ttu-id="24647-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24647-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24647-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="24647-108">Attributes and Elements</span></span>  
 <span data-ttu-id="24647-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24647-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24647-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="24647-110">Attributes</span></span>  
 <span data-ttu-id="24647-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="24647-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24647-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="24647-112">Child Elements</span></span>  
  
|<span data-ttu-id="24647-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="24647-113">**Element**</span></span>|<span data-ttu-id="24647-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="24647-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="24647-115">add</span><span class="sxs-lookup"><span data-stu-id="24647-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="24647-116">Uygulamaya bir kimlik doğrulama modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="24647-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="24647-117">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="24647-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="24647-118">Tüm kimlik doğrulama modüllerini uygulamadan temizler.</span><span class="sxs-lookup"><span data-stu-id="24647-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="24647-119">remove</span><span class="sxs-lookup"><span data-stu-id="24647-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="24647-120">Bir kimlik doğrulama modülünü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="24647-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24647-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="24647-121">Parent Elements</span></span>  
  
|<span data-ttu-id="24647-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="24647-122">**Element**</span></span>|<span data-ttu-id="24647-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="24647-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="24647-124">system.net</span><span class="sxs-lookup"><span data-stu-id="24647-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="24647-125">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="24647-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24647-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24647-126">Remarks</span></span>  
 <span data-ttu-id="24647-127">`authenticationModule` öğesi, bir sunucusuyla kimlik doğrulama işlemini gerçekleştiren kimlik doğrulama modüllerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="24647-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="24647-128">Bir kimlik doğrulama modülünün <xref:System.Net.IAuthenticationModule> arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="24647-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="24647-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="24647-129">Configuration Files</span></span>  
 <span data-ttu-id="24647-130">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24647-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24647-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="24647-131">Example</span></span>  
 <span data-ttu-id="24647-132">Aşağıdaki örnek bir kimlik doğrulama modülünü mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="24647-132">The following example enables an authentication module.</span></span> <span data-ttu-id="24647-133">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="24647-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24647-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24647-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="24647-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="24647-135">Network Settings Schema</span></span>](index.md)
