---
title: "&lt;ekleme&gt; öğesi webRequestModules (ağ ayarları) için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9b7d2c0f52ea42fcb98be149ab005cd67c2db46a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="99b0e-102">&lt;ekleme&gt; öğesi webRequestModules (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="99b0e-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="99b0e-103">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="99b0e-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="99b0e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="99b0e-104">\<configuration></span></span>  
<span data-ttu-id="99b0e-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="99b0e-105">\<system.net></span></span>  
<span data-ttu-id="99b0e-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="99b0e-106">\<webRequestModules></span></span>  
<span data-ttu-id="99b0e-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="99b0e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b0e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99b0e-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99b0e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="99b0e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="99b0e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99b0e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99b0e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99b0e-111">Attributes</span></span>  
  
|<span data-ttu-id="99b0e-112">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="99b0e-112">**Attribute**</span></span>|<span data-ttu-id="99b0e-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="99b0e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="99b0e-114">Bu Web isteği modülü tarafından işlenen isteklerin için URI öneki.</span><span class="sxs-lookup"><span data-stu-id="99b0e-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="99b0e-115">Tam olarak nitelenmiş tür adını (belirttiği <xref:System.Type.FullName%2A> özelliği) ve derleme adının (belirttiği <xref:System.Reflection.Assembly.FullName%2A> özelliği), bu Web isteği modülü uygulayan bir virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="99b0e-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99b0e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="99b0e-116">Child Elements</span></span>  
 <span data-ttu-id="99b0e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="99b0e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99b0e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="99b0e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="99b0e-119">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="99b0e-119">**Element**</span></span>|<span data-ttu-id="99b0e-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="99b0e-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="99b0e-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="99b0e-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="99b0e-122">Ağ ana bilgisayarlardan bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="99b0e-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99b0e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99b0e-123">Remarks</span></span>  
 <span data-ttu-id="99b0e-124">`prefix` Öznitelik belirtilen Web isteği modülü kullanan URI öneki tanımlar.</span><span class="sxs-lookup"><span data-stu-id="99b0e-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="99b0e-125">Web isteği modülleri HTTP veya FTP gibi belirli bir iletişim kuralı işlemek için genellikle kayıtlı ancak belirli sunucu veya bir sunucudaki yolu bir isteği işlemek üzere kaydettirilmiş.</span><span class="sxs-lookup"><span data-stu-id="99b0e-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="99b0e-126">Web isteği modülü bir URI eşleşen Önek geçirilir oluşturulduğunda <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99b0e-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="99b0e-127">Değeri `prefix` özniteliği geçerli bir URI--Örneğin, "http" veya "http://www.contoso.com" başında karakter olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99b0e-127">The value for the `prefix` attribute should be the leading characters of a valid URI --for example, "http", or "http://www.contoso.com".</span></span>  
  
 <span data-ttu-id="99b0e-128">Değeri `type` özniteliği geçerli bir tür adı ve karşılık gelen derleme adı, virgülle ayrılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99b0e-128">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma .</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="99b0e-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="99b0e-129">Configuration Files</span></span>  
 <span data-ttu-id="99b0e-130">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99b0e-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99b0e-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="99b0e-131">Example</span></span>  
 <span data-ttu-id="99b0e-132">Aşağıdaki örnek, HTTP için özel bir Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="99b0e-132">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="99b0e-133">Belirtilen modül için doğru değerlerle sürüm ve PublicKeyToken için değerleri değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="99b0e-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99b0e-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99b0e-134">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="99b0e-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="99b0e-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
