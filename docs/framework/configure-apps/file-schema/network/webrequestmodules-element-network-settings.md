---
title: <webRequestModules> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: c30a7a0bcce62c99d7c1ec0ff17389b8c2cd2f17
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663938"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="d1f29-102">\<webRequestModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="d1f29-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="d1f29-103">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d1f29-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="d1f29-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d1f29-104">\<configuration></span></span>  
<span data-ttu-id="d1f29-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d1f29-105">\<system.net></span></span>  
<span data-ttu-id="d1f29-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="d1f29-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1f29-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1f29-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1f29-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1f29-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d1f29-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1f29-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1f29-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d1f29-110">Attributes</span></span>  
 <span data-ttu-id="d1f29-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="d1f29-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1f29-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1f29-112">Child Elements</span></span>  
  
|<span data-ttu-id="d1f29-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="d1f29-113">**Element**</span></span>|<span data-ttu-id="d1f29-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d1f29-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d1f29-115">add</span><span class="sxs-lookup"><span data-stu-id="d1f29-115">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="d1f29-116">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="d1f29-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="d1f29-117">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="d1f29-117">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="d1f29-118">Tüm kayıtlı Web isteği modüllerini uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d1f29-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="d1f29-119">remove</span><span class="sxs-lookup"><span data-stu-id="d1f29-119">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="d1f29-120">Uygulamadan özel bir Web istek modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d1f29-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1f29-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1f29-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d1f29-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="d1f29-122">**Element**</span></span>|<span data-ttu-id="d1f29-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d1f29-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d1f29-124">system.net</span><span class="sxs-lookup"><span data-stu-id="d1f29-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="d1f29-125">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d1f29-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1f29-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1f29-126">Remarks</span></span>  
 <span data-ttu-id="d1f29-127">Öğesi `webRequestModules` , ağ konaklarına bilgi <xref:System.Net.WebRequest> isteklerini işlemek üzere sınıfının alt öğelerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d1f29-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="d1f29-128">Web isteği modülleri <xref:System.Net.IWebRequestCreate> arabirimini gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="d1f29-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="d1f29-129">.NET Framework,, ve `http://` `https://` `file://`ile başlayan URI 'ler için Web isteği modülleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d1f29-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="d1f29-130">Varsayılan modülleri yalnızca yapılandırma dosyasına özel bir modül kaydederek geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1f29-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d1f29-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d1f29-131">Configuration Files</span></span>  
 <span data-ttu-id="d1f29-132">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1f29-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1f29-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1f29-133">Example</span></span>  
 <span data-ttu-id="d1f29-134">Aşağıdaki örnek varsayılan HTTP modülünü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d1f29-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="d1f29-135">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d1f29-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1f29-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1f29-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="d1f29-137">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d1f29-137">Network Settings Schema</span></span>](index.md)
