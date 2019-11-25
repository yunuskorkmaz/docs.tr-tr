---
title: <proxy> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 5f327a2bb4fe316497614f14669907d514c20654
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089188"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="e8bef-102">\<proxy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="e8bef-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="e8bef-103">Bir ara sunucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8bef-103">Defines a proxy server.</span></span>  

<span data-ttu-id="e8bef-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e8bef-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e8bef-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="e8bef-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e8bef-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e8bef-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="e8bef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<proxy >**</span><span class="sxs-lookup"><span data-stu-id="e8bef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e8bef-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8bef-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8bef-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8bef-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e8bef-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8bef-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8bef-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e8bef-111">Attributes</span></span>  
  
|<span data-ttu-id="e8bef-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="e8bef-112">**Attribute**</span></span>|<span data-ttu-id="e8bef-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e8bef-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="e8bef-114">Proxy 'nin otomatik olarak algılanıp algılanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8bef-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="e8bef-115">Varsayılan değer `unspecified` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e8bef-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="e8bef-116">Yerel kaynaklar için proxy 'nin atlanıp atlanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8bef-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="e8bef-117">Yerel kaynaklar yerel sunucuyu (`http://localhost`, `http://loopback` veya `http://127.0.0.1`) ve nokta olmayan bir URI 'yi (`http://webserver`) içerir.</span><span class="sxs-lookup"><span data-stu-id="e8bef-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="e8bef-118">Varsayılan değer `unspecified` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e8bef-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="e8bef-119">Kullanılacak proxy URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8bef-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="e8bef-120">Yapılandırma betiğinin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8bef-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="e8bef-121">Bu öznitelikle `bypassonlocal` özniteliğini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e8bef-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="e8bef-122">Internet Explorer proxy ayarlarının kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8bef-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="e8bef-123">`true`olarak ayarlanırsa, sonraki öznitelikler Internet Explorer proxy ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e8bef-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="e8bef-124">Varsayılan değer `unspecified` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e8bef-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8bef-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8bef-125">Child Elements</span></span>  
 <span data-ttu-id="e8bef-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="e8bef-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8bef-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8bef-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e8bef-128">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="e8bef-128">**Element**</span></span>|<span data-ttu-id="e8bef-129">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e8bef-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e8bef-130">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="e8bef-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="e8bef-131">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e8bef-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="e8bef-132">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="e8bef-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8bef-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8bef-133">Remarks</span></span>  
 <span data-ttu-id="e8bef-134">`proxy` öğesi bir uygulama için ara sunucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8bef-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="e8bef-135">Yapılandırma dosyasında bu öğe eksikse .NET Framework, Internet Explorer 'daki proxy ayarlarını kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="e8bef-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="e8bef-136">`proxyaddress` özniteliğinin değeri iyi biçimlendirilmiş bir Tekdüzen Kaynak göstergesi (URI) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8bef-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="e8bef-137">`scriptLocation` özniteliği, proxy yapılandırma betikleri otomatik algılamayı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="e8bef-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="e8bef-138"><xref:System.Net.WebProxy> sınıfı, Internet Explorer 'da **otomatik yapılandırma betiği kullan** seçeneği belirlendiğinde bir yapılandırma betiğini (genellikle WPAD. dat olarak adlandırılır) bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="e8bef-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="e8bef-139">`bypassonlocal` herhangi bir değere ayarlanırsa, `scriptLocation` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="e8bef-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="e8bef-140">2,0 sürümüne geçiş yapan .NET Framework sürüm 1,1 uygulamaları için `usesystemdefault` özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8bef-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="e8bef-141">`proxyaddress` özniteliği geçersiz bir varsayılan proxy belirtiyorsa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e8bef-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="e8bef-142">Özel durumun <xref:System.Exception.InnerException%2A> özelliği, hatanın kök nedeni hakkında daha fazla bilgiye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8bef-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e8bef-143">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e8bef-143">Configuration Files</span></span>  
 <span data-ttu-id="e8bef-144">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8bef-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8bef-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8bef-145">Example</span></span>  
 <span data-ttu-id="e8bef-146">Aşağıdaki örnek, Internet Explorer proxy 'sinin varsayılan değerlerini kullanır, proxy adresini belirtir ve yerel erişim için ara sunucuyu atlar.</span><span class="sxs-lookup"><span data-stu-id="e8bef-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8bef-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8bef-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e8bef-148">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e8bef-148">Network Settings Schema</span></span>](index.md)
