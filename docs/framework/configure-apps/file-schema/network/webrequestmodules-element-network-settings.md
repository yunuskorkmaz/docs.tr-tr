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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154549"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="d0682-102">\<webRequestModules> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="d0682-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="d0682-103">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0682-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a><span data-ttu-id="d0682-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0682-104">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0682-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0682-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d0682-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0682-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0682-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0682-107">Attributes</span></span>  
 <span data-ttu-id="d0682-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0682-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0682-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0682-109">Child Elements</span></span>  
  
|<span data-ttu-id="d0682-110">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="d0682-110">**Element**</span></span>|<span data-ttu-id="d0682-111">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d0682-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d0682-112">add</span><span class="sxs-lookup"><span data-stu-id="d0682-112">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="d0682-113">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="d0682-113">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="d0682-114">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="d0682-114">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="d0682-115">Tüm kayıtlı Web isteği modüllerini uygulamadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d0682-115">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="d0682-116">temizlenmesine</span><span class="sxs-lookup"><span data-stu-id="d0682-116">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="d0682-117">Uygulamadan özel bir Web istek modülünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d0682-117">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0682-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0682-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d0682-119">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="d0682-119">**Element**</span></span>|<span data-ttu-id="d0682-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d0682-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d0682-121">system.net</span><span class="sxs-lookup"><span data-stu-id="d0682-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="d0682-122">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d0682-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0682-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0682-123">Remarks</span></span>  
 <span data-ttu-id="d0682-124">`webRequestModules`Öğesi, <xref:System.Net.WebRequest> ağ konaklarına bilgi isteklerini işlemek üzere sınıfının alt öğelerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d0682-124">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="d0682-125">Web isteği modülleri <xref:System.Net.IWebRequestCreate> arabirimini gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="d0682-125">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="d0682-126">.NET Framework,, ve ile başlayan URI 'Ler için Web isteği modülleri içerir `http://` `https://` `file://` .</span><span class="sxs-lookup"><span data-stu-id="d0682-126">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="d0682-127">Varsayılan modülleri yalnızca yapılandırma dosyasına özel bir modül kaydederek geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0682-127">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d0682-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d0682-128">Configuration Files</span></span>  
 <span data-ttu-id="d0682-129">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0682-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0682-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0682-130">Example</span></span>  
 <span data-ttu-id="d0682-131">Aşağıdaki örnek varsayılan HTTP modülünü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d0682-131">The following example registers the default HTTP module.</span></span> <span data-ttu-id="d0682-132">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d0682-132">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0682-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0682-133">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="d0682-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d0682-134">Network Settings Schema</span></span>](index.md)
