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
ms.openlocfilehash: 5fba4bfa14642092dbb7c0153bcd92160a62b12b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929266"
---
# <a name="ltproxygt-element-network-settings"></a><span data-ttu-id="f4aac-102">&lt;Proxy&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="f4aac-102">&lt;proxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="f4aac-103">Bir proxy sunucusu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4aac-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="f4aac-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f4aac-104">\<configuration></span></span>  
<span data-ttu-id="f4aac-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f4aac-105">\<system.net></span></span>  
<span data-ttu-id="f4aac-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="f4aac-106">\<defaultProxy></span></span>  
<span data-ttu-id="f4aac-107">\<Proxy ></span><span class="sxs-lookup"><span data-stu-id="f4aac-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4aac-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4aac-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4aac-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4aac-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f4aac-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4aac-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4aac-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4aac-111">Attributes</span></span>  
  
|<span data-ttu-id="f4aac-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="f4aac-112">**Attribute**</span></span>|<span data-ttu-id="f4aac-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f4aac-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="f4aac-114">Proxy otomatik olarak algılanır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="f4aac-115">Varsayılan değer `unspecified` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="f4aac-116">Proxy için yerel kaynak atlanır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="f4aac-117">Yerel kaynaklar yerel sunucuyu içerir (`http://localhost`, `http://loopback`, veya `http://127.0.0.1`) ve bir nokta olmadan bir URI (`http://webserver`).</span><span class="sxs-lookup"><span data-stu-id="f4aac-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="f4aac-118">Varsayılan değer `unspecified` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="f4aac-119">Proxy kullanmak için URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="f4aac-120">Yapılandırma betiğini konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="f4aac-121">Kullanmayın `bypassonlocal` özniteliği bu öznitelikle.</span><span class="sxs-lookup"><span data-stu-id="f4aac-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="f4aac-122">Internet Explorer proxy ayarlarının kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="f4aac-123">Varsa kümesine `true`, sonraki öznitelikleri, Internet Explorer proxy ayarlarını geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="f4aac-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="f4aac-124">Varsayılan değer `unspecified` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4aac-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4aac-125">Child Elements</span></span>  
 <span data-ttu-id="f4aac-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="f4aac-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4aac-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4aac-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f4aac-128">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="f4aac-128">**Element**</span></span>|<span data-ttu-id="f4aac-129">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f4aac-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f4aac-130">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="f4aac-130">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="f4aac-131">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f4aac-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="f4aac-132">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="f4aac-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4aac-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4aac-133">Remarks</span></span>  
 <span data-ttu-id="f4aac-134">`proxy` Öğesi, bir uygulama için bir proxy sunucusu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4aac-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="f4aac-135">Bu öğe yapılandırma dosyasından eksikse, .NET Framework Internet Explorer'ın proxy ayarlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4aac-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="f4aac-136">Değeri `proxyaddress` özniteliği bir biçimlendirilmiş Tekdüzen Kaynak göstergesi'nı (URI) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4aac-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="f4aac-137">`scriptLocation` Öznitelik proxy yapılandırma betiklerini otomatik algılanması için ifade eder.</span><span class="sxs-lookup"><span data-stu-id="f4aac-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="f4aac-138"><xref:System.Net.WebProxy> Sınıfı, bir yapılandırma betiği (genellikle adlandırılmış Wpad.dat) ne zaman bulunacak deneyecek **otomatik yapılandırma betiği kullan** seçeneği, Internet Explorer'da belirlenir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="f4aac-139">Varsa `bypassonlocal` herhangi bir değere ayarlanmış `scriptLocation` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="f4aac-140">Kullanım `usesystemdefault` 2.0 sürümüne geçiş yapıyorsanız, .NET Framework sürüm 1.1 uygulamaları için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f4aac-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="f4aac-141">Bir özel durum `proxyaddress` özniteliği geçersiz varsayılan proxy belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="f4aac-142"><xref:System.Exception.InnerException%2A> Özel durum özelliği, hatanın kök nedeni hakkında daha fazla bilgi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f4aac-143">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f4aac-143">Configuration Files</span></span>  
 <span data-ttu-id="f4aac-144">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4aac-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4aac-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4aac-145">Example</span></span>  
 <span data-ttu-id="f4aac-146">Aşağıdaki örnek, Internet Explorer proxy varsayılanlarından kullanır, proxy adresi belirtir ve yerel erişim proxy atlar.</span><span class="sxs-lookup"><span data-stu-id="f4aac-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4aac-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4aac-147">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="f4aac-148">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f4aac-148">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
