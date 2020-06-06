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
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155030"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="fc66c-102">webRequestModules için \<add> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="fc66c-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="fc66c-103">Uygulamaya özel bir Web isteği modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="fc66c-103">Adds a custom Web request module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="fc66c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc66c-104">Syntax</span></span>  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc66c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc66c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fc66c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc66c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc66c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fc66c-107">Attributes</span></span>  
  
|<span data-ttu-id="fc66c-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="fc66c-108">**Attribute**</span></span>|<span data-ttu-id="fc66c-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="fc66c-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="fc66c-110">Bu Web isteği modülü tarafından işlenen istekler için URI ön eki.</span><span class="sxs-lookup"><span data-stu-id="fc66c-110">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="fc66c-111"><xref:System.Type.FullName%2A>Bu Web istek modülünü uygulayan, tam tür adı (özelliği tarafından gösterilen) ve derleme adı (özelliği ile belirtilir <xref:System.Reflection.Assembly.FullName%2A> ), virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="fc66c-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc66c-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc66c-112">Child Elements</span></span>  
 <span data-ttu-id="fc66c-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="fc66c-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc66c-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc66c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fc66c-115">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="fc66c-115">**Element**</span></span>|<span data-ttu-id="fc66c-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="fc66c-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fc66c-117">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="fc66c-117">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="fc66c-118">Ağ konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc66c-118">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc66c-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc66c-119">Remarks</span></span>  
 <span data-ttu-id="fc66c-120">`prefix`Özniteliği belirtilen Web istek modülünü kullanan URI önekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fc66c-120">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="fc66c-121">Web isteği modülleri, genellikle HTTP veya FTP gibi belirli bir protokolü işlemek için kaydedilir, ancak bir sunucudaki belirli bir sunucuya veya yola yönelik bir isteği işlemek için kayıt yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc66c-121">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="fc66c-122">Yöntemine bir URI eşleştirme öneki geçirildiğinde Web istek modülü oluşturulur <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fc66c-122">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="fc66c-123">`prefix`Özniteliğin değeri geçerli BIR URI 'nin baştaki karakterleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc66c-123">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="fc66c-124">Örneğin `http` veya `http://www.contoso.com` olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc66c-124">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="fc66c-125">Özniteliğin değeri, `type` virgülle ayrılmış olarak geçerli bir tür adı ve karşılık gelen derleme adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc66c-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="fc66c-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="fc66c-126">Configuration Files</span></span>  
 <span data-ttu-id="fc66c-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc66c-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc66c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc66c-128">Example</span></span>  
 <span data-ttu-id="fc66c-129">Aşağıdaki örnek, HTTP için özel bir Web isteği modülü kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fc66c-129">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="fc66c-130">Version ve PublicKeyToken değerlerini belirtilen modülle ilgili doğru değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fc66c-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fc66c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc66c-131">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="fc66c-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fc66c-132">Network Settings Schema</span></span>](index.md)
