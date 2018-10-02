---
title: Proxy yapılandırması
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f4ae905b7500a8555691557b264985acf538d075
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036995"
---
# <a name="proxy-configuration"></a><span data-ttu-id="6b2ac-102">Proxy yapılandırması</span><span class="sxs-lookup"><span data-stu-id="6b2ac-102">Proxy Configuration</span></span>
<span data-ttu-id="6b2ac-103">Bir proxy sunucu kaynakları için istemci isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="6b2ac-104">Bir proxy önbelleğinden istenen kaynak döndürebilen veya kaynağının bulunduğu sunucu isteği iletir.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="6b2ac-105">Proxy, uzak sunucuya gönderilen istek sayısını azaltarak ağ performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="6b2ac-106">Proxy'leri, kaynaklara erişimi kısıtlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="6b2ac-107">Uyarlamalı proxy'ler</span><span class="sxs-lookup"><span data-stu-id="6b2ac-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="6b2ac-108">.NET Framework'teki proxy'leri iki çeşit olarak bulunur: Uyarlamalı ve statik.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="6b2ac-109">Ağ yapılandırması değiştiğinde Uyarlamalı proxy ayarlarını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="6b2ac-110">Örneğin, bir dizüstü kullanıcı bir çevirmeli ağ bağlantısı başlarsa, Uyarlamalı bir proxy bu değişikliği tanıması, bulmak, yeni bir yapılandırma betiği çalıştırın ve kendi ayarlarını uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="6b2ac-111">Uyarlamalı proxy'leri, bir yapılandırma betiği tarafından yapılandırılır (bkz [Otomatik Proxy algılama](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="6b2ac-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="6b2ac-112">Betik, bir dizi uygulama protokolleri ve her protokol için bir proxy oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="6b2ac-113">Ağ ortamınızda değişiklikler Sistem proxy yeni bir dizi gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="6b2ac-114">Bir ağ bağlantısı arıza ya da yeni bir ağ bağlantısı başlatılır, sistem uygun kaynak yeni ortama yapılandırma betiğinin keşfedin ve yeni betiği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="6b2ac-115">Kullanabileceğiniz `usesystemdefault` özniteliği [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) yapılandırma dosyanızdaki öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="6b2ac-116">`usesystemdefault` Kullanıcı için Internet Explorer proxy ayarlarını (proxy adresi, atlama listesi ve yerel atlama) statik proxy ayarlarını okunur olmadığını denetimleri özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="6b2ac-117">Bu değer ayarlanırsa `true`, Internet Explorer'dan statik proxy ayarları kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="6b2ac-118">Bu değer ise `false` veya ayarlanmadı, statik proxy ayarlarını yapılandırmada belirtilen ve Internet Explorer proxy ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="6b2ac-119">Bu değer ayrıca ayarlanmalıdır `false` veya uyarlamalı proxy'leri etkinleştirilmesi için ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="6b2ac-120">Aşağıdaki örnek, tipik Uyarlamalı proxy yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="6b2ac-121">Statik proxy'ler</span><span class="sxs-lookup"><span data-stu-id="6b2ac-121">Static Proxies</span></span>  
 <span data-ttu-id="6b2ac-122">Statik proxy'leri genellikle açıkça bir uygulama tarafından veya bir yapılandırma dosyası bir uygulama veya sistem tarafından çağrıldığında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="6b2ac-123">Statik proxy'leri, topoloji, bir şirket ağına bağlı bir masaüstü bilgisayar gibi sık değişmeyen ağlardaki yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="6b2ac-124">Çeşitli seçenekler, statik bir proxy nasıl çalıştığını denetler.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="6b2ac-125">Aşağıdakileri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6b2ac-125">You can specify the following:</span></span>  
  
-   <span data-ttu-id="6b2ac-126">Proxy adresi.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-126">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="6b2ac-127">Proxy yerel adresler için atlanmasına.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="6b2ac-128">Proxy için adresleri kümesini atlanmasına.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="6b2ac-129">Aşağıdaki tabloda, statik bir ara sunucu yapılandırma seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="6b2ac-130">Öznitelik, özellik veya yapılandırma dosyası ayarı</span><span class="sxs-lookup"><span data-stu-id="6b2ac-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="6b2ac-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b2ac-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="6b2ac-132">`proxyaddress` veya <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="6b2ac-132">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="6b2ac-133">Kullanılacak proxy adresi.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-133">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="6b2ac-134">`bypassonlocal` veya <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="6b2ac-134">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="6b2ac-135">Yerel adresler için proxy atlanır olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="6b2ac-136">`bypasslist` veya <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="6b2ac-136">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="6b2ac-137">, Normal ifadeler ile bir proxy atlama adresleri kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="6b2ac-138">Kullanıcı için Internet Explorer proxy ayarlarını (proxy adresi atlama listesine ve yerel atlama) statik proxy ayarlarını gerekip gerekmediğini okunması denetler.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="6b2ac-139">Bu değer ayarlanırsa `true`, Internet Explorer statik proxy ayarları kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="6b2ac-140">Bu değer ayarlandığında .NET Framework 2.0 `true`, Internet Explorer proxy ayarlarını yapılandırma dosyasındaki diğer proxy ayarları geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="6b2ac-141">.NET Framework 1.1, Internet Explorer proxy ayarlarının diğer proxy ayarlarını yapılandırma dosyasındaki kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="6b2ac-142">Bu değer ise `false` veya ayarlanmadı, ardından statik proxy ayarlarını yapılandırmada belirtilen ve Internet Explorer proxy ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="6b2ac-143">Bu değer ayrıca ayarlanmalıdır `false` veya uyarlamalı proxy'leri etkinleştirilmesi için ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="6b2ac-144">Aşağıdaki örnek bir genel statik proxy yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-144">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b2ac-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b2ac-145">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="6b2ac-146">Otomatik Ara Sunucu Algılama</span><span class="sxs-lookup"><span data-stu-id="6b2ac-146">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
