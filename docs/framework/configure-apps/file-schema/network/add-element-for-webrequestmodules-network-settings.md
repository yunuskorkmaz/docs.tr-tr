---
title: webRequestModules için <add> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: f99c5b0dc7eab57d4e3e86f49dbbb3228c7b7d8b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664214"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="a6059-102">\<webRequestModules için > öğesi ekleme (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="a6059-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="a6059-103">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="a6059-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="a6059-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="a6059-104">\<configuration></span></span>  
<span data-ttu-id="a6059-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a6059-105">\<system.net></span></span>  
<span data-ttu-id="a6059-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="a6059-106">\<webRequestModules></span></span>  
<span data-ttu-id="a6059-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="a6059-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6059-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6059-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6059-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6059-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a6059-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6059-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6059-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a6059-111">Attributes</span></span>  
  
|<span data-ttu-id="a6059-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="a6059-112">**Attribute**</span></span>|<span data-ttu-id="a6059-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a6059-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="a6059-114">Bu Web isteği modülü tarafından işlenen istekler için URI ön eki.</span><span class="sxs-lookup"><span data-stu-id="a6059-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="a6059-115">Bu Web istek modülünü uygulayan, tam tür adı <xref:System.Type.FullName%2A> (özelliği tarafından gösterilen) ve derleme adı ( <xref:System.Reflection.Assembly.FullName%2A> özelliği ile belirtilir), virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="a6059-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6059-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6059-116">Child Elements</span></span>  
 <span data-ttu-id="a6059-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="a6059-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6059-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6059-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a6059-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="a6059-119">**Element**</span></span>|<span data-ttu-id="a6059-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a6059-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a6059-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="a6059-121">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="a6059-122">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6059-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6059-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6059-123">Remarks</span></span>  
 <span data-ttu-id="a6059-124">`prefix` Özniteliği belirtilen Web istek modülünü kullanan URI önekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a6059-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="a6059-125">Web isteği modülleri, genellikle HTTP veya FTP gibi belirli bir protokolü işlemek için kaydedilir, ancak bir sunucudaki belirli bir sunucuya veya yola yönelik bir isteği işlemek için kayıt yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6059-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="a6059-126"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> Yöntemine bir URI eşleştirme öneki geçirildiğinde Web istek modülü oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a6059-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a6059-127">`prefix` Özniteliğin değeri geçerli bir URI 'nin baştaki karakterleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6059-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="a6059-128">Örneğin, `http` veya `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="a6059-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="a6059-129">`type` Özniteliğin değeri, virgülle ayrılmış olarak geçerli bir tür adı ve karşılık gelen derleme adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6059-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="a6059-130">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="a6059-130">Configuration Files</span></span>  
 <span data-ttu-id="a6059-131">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6059-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6059-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6059-132">Example</span></span>  
 <span data-ttu-id="a6059-133">Aşağıdaki örnek, HTTP için özel bir Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a6059-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="a6059-134">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a6059-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6059-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6059-135">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="a6059-136">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a6059-136">Network Settings Schema</span></span>](index.md)
