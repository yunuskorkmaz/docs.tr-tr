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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154796"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="6f86b-102">\<proxy> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="6f86b-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="6f86b-103">Proxy sunucusu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f86b-103">Defines a proxy server.</span></span>  

<span data-ttu-id="6f86b-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6f86b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6f86b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6f86b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="6f86b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6f86b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="6f86b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**</span><span class="sxs-lookup"><span data-stu-id="6f86b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6f86b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f86b-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f86b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f86b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6f86b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f86b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f86b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f86b-111">Attributes</span></span>  
  
|<span data-ttu-id="6f86b-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="6f86b-112">**Attribute**</span></span>|<span data-ttu-id="6f86b-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6f86b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="6f86b-114">Proxy'nin otomatik olarak algılanıp algılanmayanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f86b-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="6f86b-115">Varsayılan değer: `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="6f86b-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="6f86b-116">Proxy'nin yerel kaynaklar için atlanıp atlanıp atlılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f86b-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="6f86b-117">Yerel kaynaklar yerel sunucu`http://localhost` `http://loopback`(, `http://127.0.0.1`, veya ) ve`http://webserver`bir dönem olmadan bir URI içerir ( ).</span><span class="sxs-lookup"><span data-stu-id="6f86b-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="6f86b-118">Varsayılan değer: `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="6f86b-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="6f86b-119">Kullanılacak proxy URI'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f86b-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="6f86b-120">Yapılandırma komut dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f86b-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="6f86b-121">Özniteliği bu `bypassonlocal` öznitelik ile kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="6f86b-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="6f86b-122">Internet Explorer proxy ayarlarını kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f86b-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="6f86b-123">`true`Ayarlanırsa, sonraki öznitelikler Internet Explorer proxy ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6f86b-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="6f86b-124">Varsayılan değer: `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="6f86b-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f86b-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f86b-125">Child Elements</span></span>  
 <span data-ttu-id="6f86b-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f86b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f86b-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f86b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6f86b-128">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="6f86b-128">**Element**</span></span>|<span data-ttu-id="6f86b-129">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6f86b-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6f86b-130">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="6f86b-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="6f86b-131">Hypertext Transfer Protocol (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6f86b-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="6f86b-132">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="6f86b-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f86b-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f86b-133">Remarks</span></span>  
 <span data-ttu-id="6f86b-134">Öğe, `proxy` bir uygulama için bir proxy sunucusu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f86b-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="6f86b-135">Bu öğe yapılandırma dosyasında eksikse, .NET Framework Internet Explorer'daki proxy ayarlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f86b-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="6f86b-136">Öznitelik değeri `proxyaddress` iyi biçimlendirilmiş bir Tekdüzen Kaynak Göstergesi (URI) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f86b-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="6f86b-137">Öznitelik `scriptLocation` proxy yapılandırma komut dosyalarının otomatik algılama anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6f86b-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="6f86b-138">Sınıf, <xref:System.Net.WebProxy> Internet Explorer'da **Otomatik yapılandırma komut dosyası kullan** seçeneği seçildiğinde bir yapılandırma komut dosyası (genellikle Wpad.dat olarak adlandırılır) bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="6f86b-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="6f86b-139">Herhangi `bypassonlocal` bir değere `scriptLocation` ayarlanmışsa, yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="6f86b-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="6f86b-140">`usesystemdefault` .NET Framework sürüm 1.1 uygulamalarının sürüm 2.0'a geçiş yapan özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f86b-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="6f86b-141">`proxyaddress` Öznitelik geçersiz bir varsayılan proxy belirtirse bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="6f86b-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="6f86b-142">Özel <xref:System.Exception.InnerException%2A> durum özelliği, hatanın temel nedeni hakkında daha fazla bilgiye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f86b-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6f86b-143">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6f86b-143">Configuration Files</span></span>  
 <span data-ttu-id="6f86b-144">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f86b-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f86b-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f86b-145">Example</span></span>  
 <span data-ttu-id="6f86b-146">Aşağıdaki örnek, Internet Explorer proxy'sinden varsayılanları kullanır, proxy adresini belirtir ve yerel erişim için proxy'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="6f86b-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f86b-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f86b-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="6f86b-148">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6f86b-148">Network Settings Schema</span></span>](index.md)
