---
title: '&lt;webRequestModules&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 1d421009e8b2e0d4074679939092180c6037a0c7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200450"
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a><span data-ttu-id="f7522-102">&lt;webRequestModules&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="f7522-102">&lt;webRequestModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="f7522-103">Ağ konaklarından bilgi istemek için modüller belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7522-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="f7522-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f7522-104">\<configuration></span></span>  
<span data-ttu-id="f7522-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f7522-105">\<system.net></span></span>  
<span data-ttu-id="f7522-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="f7522-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7522-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7522-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7522-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7522-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f7522-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7522-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7522-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f7522-110">Attributes</span></span>  
 <span data-ttu-id="f7522-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="f7522-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7522-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7522-112">Child Elements</span></span>  
  
|<span data-ttu-id="f7522-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="f7522-113">**Element**</span></span>|<span data-ttu-id="f7522-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f7522-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f7522-115">add</span><span class="sxs-lookup"><span data-stu-id="f7522-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="f7522-116">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="f7522-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="f7522-117">Temizle</span><span class="sxs-lookup"><span data-stu-id="f7522-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="f7522-118">Tüm kayıtlı Web isteği modül uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f7522-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="f7522-119">remove</span><span class="sxs-lookup"><span data-stu-id="f7522-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="f7522-120">Özel bir Web isteği modülü uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f7522-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7522-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7522-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f7522-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="f7522-122">**Element**</span></span>|<span data-ttu-id="f7522-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f7522-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f7522-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="f7522-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="f7522-125">.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="f7522-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7522-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7522-126">Remarks</span></span>  
 <span data-ttu-id="f7522-127">`webRequestModules` Öğenin alt öğeleri kaydeder <xref:System.Net.WebRequest> ağ Konaklara bilgi isteklerini işlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f7522-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="f7522-128">Web isteği modülleri uygulanmalı <xref:System.Net.IWebRequestCreate> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f7522-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="f7522-129">.NET Framework ile başlayan bir URI'leri için Web isteği modüllerini içerir `http://`, `https://`, ve `file://`.</span><span class="sxs-lookup"><span data-stu-id="f7522-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="f7522-130">Yapılandırma dosyasında özel bir modülü yalnızca kaydederek varsayılan modülleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7522-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f7522-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f7522-131">Configuration Files</span></span>  
 <span data-ttu-id="f7522-132">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7522-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7522-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7522-133">Example</span></span>  
 <span data-ttu-id="f7522-134">Aşağıdaki örnek, varsayılan HTTP modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f7522-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="f7522-135">Belirtilen modül için doğru değerlerle PublicKeyToken ve Version değerleri değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f7522-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7522-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7522-136">See Also</span></span>  
- <xref:System.Net.WebRequest>  
- <xref:System.Net.IWebRequestCreate>  
- [<span data-ttu-id="f7522-137">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f7522-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
