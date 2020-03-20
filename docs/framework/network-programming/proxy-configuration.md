---
title: Ara Sunucu Yapılandırma
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
ms.openlocfilehash: 1fbfe25b90e810ff96924a2341582ff3f5ee5e5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047351"
---
# <a name="proxy-configuration"></a><span data-ttu-id="08aca-102">Ara Sunucu Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="08aca-102">Proxy Configuration</span></span>
<span data-ttu-id="08aca-103">Proxy sunucusu, istemci kaynakları isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="08aca-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="08aca-104">Proxy, istenen kaynağı önbelleğinden döndürebilir veya isteği kaynağın bulunduğu sunucuya iletebilir.</span><span class="sxs-lookup"><span data-stu-id="08aca-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="08aca-105">Ekseksiler, uzak sunuculara gönderilen istek sayısını azaltarak ağ performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="08aca-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="08aca-106">Ekseksitler, kaynaklara erişimi kısıtlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08aca-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="08aca-107">Adaptif Proxies</span><span class="sxs-lookup"><span data-stu-id="08aca-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="08aca-108">.NET Framework'de yakınlıklar iki çeşitten gelir: uyarlanabilir ve statik.</span><span class="sxs-lookup"><span data-stu-id="08aca-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="08aca-109">Uyarlanabilir yakınlıklar, ağ yapılandırması değiştiğinde ayarlarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="08aca-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="08aca-110">Örneğin, bir dizüstü bilgisayar kullanıcısı çevirmeli ağ bağlantısı başlatırsa, uyarlanabilir bir proxy bu değişikliği tanır, yeni yapılandırma komut dosyasını keşfeder ve çalıştırAbilir ve ayarlarını uygun şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="08aca-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="08aca-111">Uyarlanabilir proxy'ler bir yapılandırma komut dosyası tarafından yapılandırılır (bkz. [Otomatik Proxy Algılama).](automatic-proxy-detection.md)</span><span class="sxs-lookup"><span data-stu-id="08aca-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="08aca-112">Komut dosyası, her protokol için bir uygulama protokolü kümesi ve proxy oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08aca-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="08aca-113">Ağ ortamındaki değişiklikler, sistemin yeni bir yakınlık kümesi kullanmasını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="08aca-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="08aca-114">Bir ağ bağlantısı kapatılırsa veya yeni bir ağ bağlantısı başlatılması durumunda, sistemin yapılandırma komut dosyasının uygun kaynağını yeni ortamda bulması ve yeni komut dosyasını çalıştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08aca-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="08aca-115">Yapılandırma dosyanızdaki `usesystemdefault` öğenin [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08aca-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="08aca-116">Öznitelik, `usesystemdefault` statik proxy ayarlarının (proxy adresi, bypass listesi ve yerel deki bypass) kullanıcı için Internet Explorer proxy ayarlarından okunup okunmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="08aca-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="08aca-117">Bu değer `true`ayarlanmışsa, Internet Explorer'ın statik proxy ayarları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08aca-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="08aca-118">Bu değer `false` ayarlanmış sa veya ayarlanmamışsa, statik proxy ayarları yapılandırmada belirtilebilir ve Internet Explorer proxy ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="08aca-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="08aca-119">Uyarlanabilir yakınlıkların etkinleştirilmesi için bu değerin ayarlanmaması `false` veya ayarlanmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08aca-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="08aca-120">Aşağıdaki örnek, tipik bir uyarlanabilir proxy yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="08aca-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="08aca-121">Statik Proxies</span><span class="sxs-lookup"><span data-stu-id="08aca-121">Static Proxies</span></span>  
 <span data-ttu-id="08aca-122">Statik ekseksenler genellikle bir uygulama tarafından veya bir yapılandırma dosyası bir uygulama veya sistem tarafından çağrıldığında açıkça yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="08aca-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="08aca-123">Statik yakınlıklar, topolojinin şirket ağına bağlı bir masaüstü bilgisayar gibi seyrek değiştiği ağlarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="08aca-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="08aca-124">Statik proxy'nin nasıl çalıştığını çeşitli seçenekler denetler.</span><span class="sxs-lookup"><span data-stu-id="08aca-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="08aca-125">Aşağıdakileri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="08aca-125">You can specify the following:</span></span>  
  
- <span data-ttu-id="08aca-126">Vekilin adresi.</span><span class="sxs-lookup"><span data-stu-id="08aca-126">The address of the proxy.</span></span>  
  
- <span data-ttu-id="08aca-127">Proxy yerel adresler için atlalı olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="08aca-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="08aca-128">Proxy adresleri kümesi için atlalı olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="08aca-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="08aca-129">Aşağıdaki tablostatik bir proxy için yapılandırma seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="08aca-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="08aca-130">Öznitelik, özellik veya yapılandırma dosya ayarı</span><span class="sxs-lookup"><span data-stu-id="08aca-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="08aca-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08aca-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="08aca-132">`proxyaddress` veya <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="08aca-132">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="08aca-133">Kullanılacak proxy adresi.</span><span class="sxs-lookup"><span data-stu-id="08aca-133">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="08aca-134">`bypassonlocal` veya <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="08aca-134">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="08aca-135">Proxy'nin yerel adresler için atlanıp atlanıp atlanıp atlılmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="08aca-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="08aca-136">`bypasslist` veya <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="08aca-136">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="08aca-137">Düzenli ifadelerle proxy'yi atlayan bir adres kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="08aca-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="08aca-138">Statik proxy ayarlarının (proxy adresi, bypass listesi ve yerel deki bypass) kullanıcı için Internet Explorer proxy ayarlarından okunup okunmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="08aca-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="08aca-139">Bu değer `true`,internet explorer statik proxy ayarları olarak ayarlanırsa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08aca-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="08aca-140">.NET Framework 2.0'da bu `true`değer ayarlandığında, Internet Explorer proxy ayarları yapılandırma dosyasındaki diğer proxy ayarları tarafından geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="08aca-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="08aca-141">.NET Framework 1.1'de, Internet Explorer proxy ayarları yapılandırma dosyasındaki diğer proxy ayarları tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="08aca-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="08aca-142">Bu değer `false` ayarlanmış sa veya ayarlanmamışsa, statik proxy ayarları yapılandırmada belirtilebilir ve Internet Explorer proxy ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="08aca-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="08aca-143">Uyarlanabilir yakınlıkların etkinleştirilmesi için bu değerin ayarlanmaması `false` veya ayarlanmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08aca-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="08aca-144">Aşağıdaki örnek, tipik bir statik proxy yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="08aca-144">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08aca-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08aca-145">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="08aca-146">Otomatik Ara Sunucu Algılama</span><span class="sxs-lookup"><span data-stu-id="08aca-146">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
