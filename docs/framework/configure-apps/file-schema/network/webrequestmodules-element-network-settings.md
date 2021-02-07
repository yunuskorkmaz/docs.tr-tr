---
description: 'Daha fazla bilgi edinin: <webRequestModules> öğesi (ağ ayarları)'
title: <webRequestModules> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 851aec2bf38910239874cb5792239a48de6efb70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698433"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="c4e6e-103">\<webRequestModules> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="c4e6e-103">\<webRequestModules> Element (Network Settings)</span></span>

<span data-ttu-id="c4e6e-104">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-104">Specifies modules to use to request information from network hosts.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a><span data-ttu-id="c4e6e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4e6e-105">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4e6e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4e6e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c4e6e-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4e6e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4e6e-108">Attributes</span></span>  

 <span data-ttu-id="c4e6e-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4e6e-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4e6e-110">Child Elements</span></span>  
  
|<span data-ttu-id="c4e6e-111">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="c4e6e-111">**Element**</span></span>|<span data-ttu-id="c4e6e-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c4e6e-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c4e6e-113">add</span><span class="sxs-lookup"><span data-stu-id="c4e6e-113">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="c4e6e-114">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-114">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="c4e6e-115">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="c4e6e-115">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="c4e6e-116">Tüm kayıtlı Web isteği modüllerini uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-116">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="c4e6e-117">temizlenmesine</span><span class="sxs-lookup"><span data-stu-id="c4e6e-117">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="c4e6e-118">Uygulamadan özel bir Web istek modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-118">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4e6e-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4e6e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c4e6e-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="c4e6e-120">**Element**</span></span>|<span data-ttu-id="c4e6e-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c4e6e-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c4e6e-122">system.net</span><span class="sxs-lookup"><span data-stu-id="c4e6e-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="c4e6e-123">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4e6e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4e6e-124">Remarks</span></span>  

 <span data-ttu-id="c4e6e-125">`webRequestModules`Öğesi, <xref:System.Net.WebRequest> ağ konaklarına bilgi isteklerini işlemek üzere sınıfının alt öğelerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-125">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="c4e6e-126">Web isteği modülleri <xref:System.Net.IWebRequestCreate> arabirimini gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-126">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="c4e6e-127">.NET Framework,, ve ile başlayan URI 'Ler için Web isteği modülleri içerir `http://` `https://` `file://` .</span><span class="sxs-lookup"><span data-stu-id="c4e6e-127">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="c4e6e-128">Varsayılan modülleri yalnızca yapılandırma dosyasına özel bir modül kaydederek geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-128">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c4e6e-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="c4e6e-129">Configuration Files</span></span>  

 <span data-ttu-id="c4e6e-130">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4e6e-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4e6e-131">Example</span></span>  

 <span data-ttu-id="c4e6e-132">Aşağıdaki örnek varsayılan HTTP modülünü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-132">The following example registers the default HTTP module.</span></span> <span data-ttu-id="c4e6e-133">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4e6e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4e6e-134">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="c4e6e-135">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="c4e6e-135">Network Settings Schema</span></span>](index.md)
