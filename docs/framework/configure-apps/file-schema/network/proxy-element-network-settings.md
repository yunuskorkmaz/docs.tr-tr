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
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154796"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="2d498-102">\<proxy> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="2d498-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="2d498-103">Bir ara sunucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d498-103">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="2d498-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d498-104">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d498-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d498-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2d498-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2d498-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d498-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2d498-107">Attributes</span></span>  
  
|<span data-ttu-id="2d498-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="2d498-108">**Attribute**</span></span>|<span data-ttu-id="2d498-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2d498-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="2d498-110">Proxy 'nin otomatik olarak algılanıp algılanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d498-110">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="2d498-111">Varsayılan değer: `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="2d498-111">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="2d498-112">Yerel kaynaklar için proxy 'nin atlanıp atlanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d498-112">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="2d498-113">Yerel sunucu ( `http://localhost` , `http://loopback` , veya `http://127.0.0.1` ) ve nokta () olmayan bir URI 'yi içerir `http://webserver` .</span><span class="sxs-lookup"><span data-stu-id="2d498-113">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="2d498-114">Varsayılan değer: `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="2d498-114">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="2d498-115">Kullanılacak proxy URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d498-115">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="2d498-116">Yapılandırma betiğinin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d498-116">Specifies the location of the configuration script.</span></span> <span data-ttu-id="2d498-117">`bypassonlocal`Bu öznitelikle özniteliğini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2d498-117">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="2d498-118">Internet Explorer proxy ayarlarının kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d498-118">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="2d498-119">Olarak ayarlanırsa `true` , sonraki öznitelikler Internet Explorer proxy ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2d498-119">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="2d498-120">Varsayılan değer: `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="2d498-120">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d498-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d498-121">Child Elements</span></span>  
 <span data-ttu-id="2d498-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d498-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d498-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d498-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2d498-124">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="2d498-124">**Element**</span></span>|<span data-ttu-id="2d498-125">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2d498-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2d498-126">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="2d498-126">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="2d498-127">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2d498-127">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="2d498-128">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="2d498-128">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d498-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d498-129">Remarks</span></span>  
 <span data-ttu-id="2d498-130">`proxy`Öğesi, bir uygulama için ara sunucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d498-130">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="2d498-131">Yapılandırma dosyasında bu öğe eksikse .NET Framework, Internet Explorer 'daki proxy ayarlarını kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="2d498-131">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="2d498-132">`proxyaddress`Özniteliğin değeri iyi biçimlendirilmiş bir Tekdüzen Kaynak göstergesi (URI) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d498-132">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="2d498-133">`scriptLocation`Öznitelik, proxy yapılandırma betikleri otomatik olarak algılanmasını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="2d498-133">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="2d498-134"><xref:System.Net.WebProxy>Bu sınıf, Internet Explorer 'da **otomatik yapılandırma betiği kullan** seçeneği belirlendiğinde bir yapılandırma betiğini (genellikle WPAD. dat olarak adlandırılır) bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="2d498-134">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="2d498-135">`bypassonlocal`Herhangi bir değere ayarlanırsa, `scriptLocation` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="2d498-135">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="2d498-136">`usesystemdefault`2,0 sürümüne geçiş yapan .NET Framework sürüm 1,1 uygulamaları için özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2d498-136">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="2d498-137">`proxyaddress`Öznitelik geçersiz bir varsayılan proxy belirtiyorsa bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="2d498-137">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="2d498-138"><xref:System.Exception.InnerException%2A>Özel durum üzerindeki özelliği, hatanın kök nedeni hakkında daha fazla bilgi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="2d498-138">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2d498-139">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="2d498-139">Configuration Files</span></span>  
 <span data-ttu-id="2d498-140">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2d498-140">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d498-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d498-141">Example</span></span>  
 <span data-ttu-id="2d498-142">Aşağıdaki örnek, Internet Explorer proxy 'sinin varsayılan değerlerini kullanır, proxy adresini belirtir ve yerel erişim için ara sunucuyu atlar.</span><span class="sxs-lookup"><span data-stu-id="2d498-142">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d498-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d498-143">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="2d498-144">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2d498-144">Network Settings Schema</span></span>](index.md)
