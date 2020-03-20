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
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154549"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="80312-102">\<webRequestModules> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="80312-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="80312-103">Ağ ana bilgisayarlarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="80312-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[<span data-ttu-id="80312-104">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="80312-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="80312-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="80312-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="80312-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="80312-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80312-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80312-107">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80312-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="80312-108">Attributes and Elements</span></span>  
 <span data-ttu-id="80312-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80312-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80312-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80312-110">Attributes</span></span>  
 <span data-ttu-id="80312-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="80312-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80312-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="80312-112">Child Elements</span></span>  
  
|<span data-ttu-id="80312-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="80312-113">**Element**</span></span>|<span data-ttu-id="80312-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="80312-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="80312-115">Ekle</span><span class="sxs-lookup"><span data-stu-id="80312-115">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="80312-116">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="80312-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="80312-117">Temizleyin</span><span class="sxs-lookup"><span data-stu-id="80312-117">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="80312-118">Tüm kayıtlı Web istek modüllerini uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="80312-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="80312-119">Kaldırmak</span><span class="sxs-lookup"><span data-stu-id="80312-119">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="80312-120">Özel bir Web isteği modüllerini uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="80312-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80312-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="80312-121">Parent Elements</span></span>  
  
|<span data-ttu-id="80312-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="80312-122">**Element**</span></span>|<span data-ttu-id="80312-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="80312-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="80312-124">system.net</span><span class="sxs-lookup"><span data-stu-id="80312-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="80312-125">.NET Framework'ün ağa nasıl bağladığını belirten ayarlar içerir.</span><span class="sxs-lookup"><span data-stu-id="80312-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80312-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80312-126">Remarks</span></span>  
 <span data-ttu-id="80312-127">Öğe, `webRequestModules` ağ ana bilgisayarlarına bilgi isteklerini <xref:System.Net.WebRequest> işlemek için sınıfın torunlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="80312-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="80312-128">Web istek modülleri <xref:System.Net.IWebRequestCreate> arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="80312-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="80312-129">.NET Framework, URI'ler için `http://`,, `https://`ve `file://`.</span><span class="sxs-lookup"><span data-stu-id="80312-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="80312-130">Varsayılan modülleri yalnızca yapılandırma dosyasına özel bir modül kaydederek geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80312-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="80312-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="80312-131">Configuration Files</span></span>  
 <span data-ttu-id="80312-132">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="80312-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80312-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="80312-133">Example</span></span>  
 <span data-ttu-id="80312-134">Aşağıdaki örnekte varsayılan HTTP modülü kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="80312-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="80312-135">Sürüm ve PublicKeyToken değerlerini belirtilen modül için doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="80312-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="80312-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80312-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="80312-137">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="80312-137">Network Settings Schema</span></span>](index.md)
