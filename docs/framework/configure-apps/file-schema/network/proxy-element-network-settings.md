---
title: '&lt;Proxy&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8d2e224f710a1f344623440f29c2c6e0e9bd661e
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37072520"
---
# <a name="ltproxygt-element-network-settings"></a><span data-ttu-id="6ef18-102">&lt;Proxy&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="6ef18-102">&lt;proxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="6ef18-103">Bir proxy sunucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6ef18-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="6ef18-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="6ef18-104">\<configuration></span></span>  
<span data-ttu-id="6ef18-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6ef18-105">\<system.net></span></span>  
<span data-ttu-id="6ef18-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="6ef18-106">\<defaultProxy></span></span>  
<span data-ttu-id="6ef18-107">\<Proxy ></span><span class="sxs-lookup"><span data-stu-id="6ef18-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ef18-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ef18-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ef18-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6ef18-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6ef18-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6ef18-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ef18-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6ef18-111">Attributes</span></span>  
  
|<span data-ttu-id="6ef18-112">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="6ef18-112">**Attribute**</span></span>|<span data-ttu-id="6ef18-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6ef18-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="6ef18-114">Proxy otomatik olarak algılanır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="6ef18-115">Varsayılan değer `unspecified` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="6ef18-116">Proxy için yerel kaynak atlanır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="6ef18-117">Yerel kaynaklar dahil yerel sunucuyu (`http://localhost`, `http://loopback`, veya `http://127.0.0.1`) ve bir nokta olmadan bir URI (`http://webserver`).</span><span class="sxs-lookup"><span data-stu-id="6ef18-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="6ef18-118">Varsayılan değer `unspecified` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="6ef18-119">Proxy kullanmak için URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="6ef18-120">Yapılandırma komut dosyası konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-120">Specifies the location of the configuration script.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="6ef18-121">Internet Explorer proxy ayarlarının kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-121">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="6ef18-122">Varsa kümesine `true`, sonraki öznitelikleri Internet Explorer proxy ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6ef18-122">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="6ef18-123">Varsayılan değer `unspecified` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-123">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ef18-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6ef18-124">Child Elements</span></span>  
 <span data-ttu-id="6ef18-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="6ef18-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ef18-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6ef18-126">Parent Elements</span></span>  
  
|<span data-ttu-id="6ef18-127">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="6ef18-127">**Element**</span></span>|<span data-ttu-id="6ef18-128">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6ef18-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6ef18-129">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="6ef18-129">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="6ef18-130">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6ef18-130">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="6ef18-131">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="6ef18-131">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ef18-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ef18-132">Remarks</span></span>  
 <span data-ttu-id="6ef18-133">`proxy` Öğe, bir uygulama için bir proxy sunucusu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6ef18-133">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="6ef18-134">Bu öğe yapılandırma dosyasından eksikse, .NET Framework Internet Explorer proxy ayarlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6ef18-134">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="6ef18-135">Değeri `proxyaddress` özniteliği bir doğru biçimlendirilmiş Tekdüzen Kaynak göstergesi'nı (URI) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ef18-135">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="6ef18-136">`scriptLocation` Özniteliği proxy yapılandırma komut otomatik algılama için başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="6ef18-136">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="6ef18-137"><xref:System.Net.WebProxy> Sınıfı bulmaya çalışır bir yapılandırma betiğini (genellikle adlandırılmış Wpad.dat) ne zaman **otomatik yapılandırma betiği kullan** seçeneği, Internet Explorer'da belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-137">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span>  
  
 <span data-ttu-id="6ef18-138">Kullanım `usesystemdefault` özniteliği sürüm 2.0 geçirme .NET Framework sürüm 1.1 uygulamaları için.</span><span class="sxs-lookup"><span data-stu-id="6ef18-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="6ef18-139">Bir özel durum `proxyaddress` özniteliği geçersiz varsayılan proxy belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="6ef18-140"><xref:System.Exception.InnerException%2A> Özel durum özelliği hatasının kök nedeni hakkında daha fazla bilgi sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ef18-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6ef18-141">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6ef18-141">Configuration Files</span></span>  
 <span data-ttu-id="6ef18-142">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6ef18-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ef18-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ef18-143">Example</span></span>  
 <span data-ttu-id="6ef18-144">Aşağıdaki örnek, varsayılan Internet Explorer proxy adlardan kullanır, proxy adresi belirtir ve yerel erişim için proxy atlar.</span><span class="sxs-lookup"><span data-stu-id="6ef18-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ef18-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ef18-145">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="6ef18-146">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6ef18-146">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
