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
ms.openlocfilehash: 76dad0c0b75d20627e9f57fd1bb467bf17c9294c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088508"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="7d224-102">webRequestModules için > öğesi ekleme \<(ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="7d224-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="7d224-103">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="7d224-103">Adds a custom Web request module to the application.</span></span>  

<span data-ttu-id="7d224-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7d224-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7d224-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="7d224-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="7d224-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webRequestModules**](webrequestmodules-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="7d224-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="7d224-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**</span><span class="sxs-lookup"><span data-stu-id="7d224-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7d224-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d224-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d224-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d224-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7d224-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d224-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d224-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d224-111">Attributes</span></span>  
  
|<span data-ttu-id="7d224-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="7d224-112">**Attribute**</span></span>|<span data-ttu-id="7d224-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="7d224-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="7d224-114">Bu Web isteği modülü tarafından işlenen istekler için URI ön eki.</span><span class="sxs-lookup"><span data-stu-id="7d224-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="7d224-115">Bu Web istek modülünü uygulayan, tam nitelikli tür adı (<xref:System.Type.FullName%2A> özelliği tarafından belirtilir) ve derleme adı (<xref:System.Reflection.Assembly.FullName%2A> özelliği tarafından belirtilir).</span><span class="sxs-lookup"><span data-stu-id="7d224-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d224-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d224-116">Child Elements</span></span>  
 <span data-ttu-id="7d224-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7d224-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d224-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d224-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7d224-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="7d224-119">**Element**</span></span>|<span data-ttu-id="7d224-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="7d224-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7d224-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="7d224-121">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="7d224-122">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d224-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d224-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d224-123">Remarks</span></span>  
 <span data-ttu-id="7d224-124">`prefix` özniteliği belirtilen Web isteği modülünü kullanan URI önekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7d224-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="7d224-125">Web isteği modülleri, genellikle HTTP veya FTP gibi belirli bir protokolü işlemek için kaydedilir, ancak bir sunucudaki belirli bir sunucuya veya yola yönelik bir isteği işlemek için kayıt yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d224-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="7d224-126">Web isteği modülü, <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemine bir URI eşleştirme öneki geçirildiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7d224-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="7d224-127">`prefix` özniteliğin değeri geçerli bir URI 'nin baştaki karakterleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d224-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="7d224-128">Örneğin, `http` veya `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="7d224-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="7d224-129">`type` özniteliğin değeri, virgülle ayrılmış olarak geçerli bir tür adı ve karşılık gelen derleme adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d224-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="7d224-130">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="7d224-130">Configuration Files</span></span>  
 <span data-ttu-id="7d224-131">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d224-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d224-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d224-132">Example</span></span>  
 <span data-ttu-id="7d224-133">Aşağıdaki örnek, HTTP için özel bir Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7d224-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="7d224-134">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7d224-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d224-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d224-135">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="7d224-136">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7d224-136">Network Settings Schema</span></span>](index.md)
