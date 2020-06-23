---
title: <proxy> Öğesi (Ağ Ayarları)
description: <proxy>Ağ ayarları öğesi .NET Framework proxy sunucu seçeneklerini tanımlar. Bu makale bir örnek içerir.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 8ae30b8c29dcf3aaa183ff295c7ee8592322797f
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141787"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="1bbb9-104">\<proxy> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="1bbb9-104">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="1bbb9-105">Bir ara sunucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-105">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="1bbb9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1bbb9-106">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="True|False|Unspecified"
  bypassonlocal="True|False|Unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="True|False|Unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bbb9-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bbb9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1bbb9-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bbb9-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1bbb9-109">Attributes</span></span>  
  
|<span data-ttu-id="1bbb9-110">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="1bbb9-110">**Attribute**</span></span>|<span data-ttu-id="1bbb9-111">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="1bbb9-111">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="1bbb9-112">Proxy 'nin otomatik olarak algılanıp algılanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-112">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="1bbb9-113">Varsayılan değer: `Unspecified`.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-113">The default value is `Unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="1bbb9-114">Yerel kaynaklar için proxy 'nin atlanıp atlanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-114">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="1bbb9-115">Yerel sunucu ( `http://localhost` , `http://loopback` , veya `http://127.0.0.1` ) ve nokta () olmayan bir URI 'yi içerir `http://webserver` .</span><span class="sxs-lookup"><span data-stu-id="1bbb9-115">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="1bbb9-116">Varsayılan değer: `Unspecified`.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-116">The default value is `Unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="1bbb9-117">Kullanılacak proxy URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-117">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="1bbb9-118">Yapılandırma betiğinin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-118">Specifies the location of the configuration script.</span></span> <span data-ttu-id="1bbb9-119">`bypassonlocal`Bu öznitelikle özniteliğini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-119">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="1bbb9-120">Internet Explorer proxy ayarlarının kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-120">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="1bbb9-121">Olarak ayarlanırsa `True` , sonraki öznitelikler Internet Explorer proxy ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-121">If set to `True`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="1bbb9-122">Varsayılan değer: `Unspecified`.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-122">The default value is `Unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bbb9-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bbb9-123">Child Elements</span></span>  
 <span data-ttu-id="1bbb9-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1bbb9-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bbb9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1bbb9-126">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="1bbb9-126">**Element**</span></span>|<span data-ttu-id="1bbb9-127">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="1bbb9-127">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1bbb9-128">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="1bbb9-128">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="1bbb9-129">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-129">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="1bbb9-130">Metin Değeri</span><span class="sxs-lookup"><span data-stu-id="1bbb9-130">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bbb9-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bbb9-131">Remarks</span></span>  
 <span data-ttu-id="1bbb9-132">`proxy`Öğesi, bir uygulama için ara sunucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-132">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="1bbb9-133">Yapılandırma dosyasında bu öğe eksikse .NET Framework, Internet Explorer 'daki proxy ayarlarını kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-133">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="1bbb9-134">`proxyaddress`Özniteliğin değeri iyi biçimlendirilmiş bir Tekdüzen Kaynak göstergesi (URI) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-134">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="1bbb9-135">`scriptLocation`Öznitelik, proxy yapılandırma betikleri otomatik olarak algılanmasını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-135">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="1bbb9-136"><xref:System.Net.WebProxy>Bu sınıf, Internet Explorer 'da **otomatik yapılandırma betiği kullan** seçeneği belirlendiğinde bir yapılandırma betiğini (genellikle WPAD. dat olarak adlandırılır) bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-136">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="1bbb9-137">`bypassonlocal`Herhangi bir değere ayarlanırsa, `scriptLocation` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-137">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="1bbb9-138">`usesystemdefault`2,0 sürümüne geçiş yapan .NET Framework sürüm 1,1 uygulamaları için özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="1bbb9-139">`proxyaddress`Öznitelik geçersiz bir varsayılan proxy belirtiyorsa bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="1bbb9-140"><xref:System.Exception.InnerException%2A>Özel durum üzerindeki özelliği, hatanın kök nedeni hakkında daha fazla bilgi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1bbb9-141">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="1bbb9-141">Configuration Files</span></span>  
 <span data-ttu-id="1bbb9-142">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bbb9-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bbb9-143">Example</span></span>  
 <span data-ttu-id="1bbb9-144">Aşağıdaki örnek, Internet Explorer proxy 'sinin varsayılan değerlerini kullanır, proxy adresini belirtir ve yerel erişim için ara sunucuyu atlar.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bbb9-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bbb9-145">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="1bbb9-146">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1bbb9-146">Network Settings Schema</span></span>](index.md)
