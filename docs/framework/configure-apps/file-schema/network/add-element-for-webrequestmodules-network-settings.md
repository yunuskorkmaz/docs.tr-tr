---
title: '&lt;ekleme&gt; webRequestModules (ağ ayarları) için'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f3c3ea63df8d99154c42e40b359180ad1065f6c5
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027019"
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="94534-102">&lt;ekleme&gt; webRequestModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="94534-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="94534-103">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="94534-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="94534-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="94534-104">\<configuration></span></span>  
<span data-ttu-id="94534-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="94534-105">\<system.net></span></span>  
<span data-ttu-id="94534-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="94534-106">\<webRequestModules></span></span>  
<span data-ttu-id="94534-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="94534-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94534-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94534-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94534-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="94534-109">Attributes and Elements</span></span>  
 <span data-ttu-id="94534-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94534-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94534-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="94534-111">Attributes</span></span>  
  
|<span data-ttu-id="94534-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="94534-112">**Attribute**</span></span>|<span data-ttu-id="94534-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="94534-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="94534-114">Bu Web isteği modülü tarafından işlenen isteklerin için URI öneki.</span><span class="sxs-lookup"><span data-stu-id="94534-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="94534-115">Tam nitelikli tür adı (belirttiği <xref:System.Type.FullName%2A> özelliği) ve derleme adı (belirttiği <xref:System.Reflection.Assembly.FullName%2A> özelliği) bu Web isteği modülü uygulayan bir virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="94534-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94534-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="94534-116">Child Elements</span></span>  
 <span data-ttu-id="94534-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="94534-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94534-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="94534-118">Parent Elements</span></span>  
  
|<span data-ttu-id="94534-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="94534-119">**Element**</span></span>|<span data-ttu-id="94534-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="94534-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="94534-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="94534-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="94534-122">Ağ konaklarından bilgi istemek için modüller belirtir.</span><span class="sxs-lookup"><span data-stu-id="94534-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94534-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94534-123">Remarks</span></span>  
 <span data-ttu-id="94534-124">`prefix` Özniteliği belirtilen Web isteği modül kullanan URI öneki tanımlar.</span><span class="sxs-lookup"><span data-stu-id="94534-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="94534-125">Web isteği modülleri, HTTP veya FTP gibi belirli bir protokol işlemek için genellikle kayıtlı ancak belirli sunucu veya bir sunucudaki yolu bir isteği işlemek için kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="94534-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="94534-126">Web isteği modülü URI'si ile eşleşen bir ön eki geçirilir oluşturulduğunda <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="94534-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="94534-127">Değeri `prefix` özniteliği önde gelen karakterleri geçerli bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94534-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="94534-128">Örneğin, `http` veya `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="94534-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="94534-129">Değeri `type` özniteliği geçerli tür adı ve karşılık gelen derleme adı, virgülle ayrılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94534-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="94534-130">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="94534-130">Configuration Files</span></span>  
 <span data-ttu-id="94534-131">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94534-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94534-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="94534-132">Example</span></span>  
 <span data-ttu-id="94534-133">Aşağıdaki örnek, HTTP için özel bir Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="94534-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="94534-134">Belirtilen modül için doğru değerlerle PublicKeyToken ve Version değerleri değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="94534-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94534-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94534-135">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="94534-136">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="94534-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
