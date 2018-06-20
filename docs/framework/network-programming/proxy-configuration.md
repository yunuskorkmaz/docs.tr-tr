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
manager: markl
ms.openlocfilehash: 6cf25d3d7dcde963f06729794716b75dffdb64ae
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207371"
---
# <a name="proxy-configuration"></a><span data-ttu-id="b01b2-102">Proxy yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b01b2-102">Proxy Configuration</span></span>
<span data-ttu-id="b01b2-103">Bir proxy sunucu kaynakları için istemci isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="b01b2-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="b01b2-104">Bir proxy, istenen kaynak, önbellekten döndürür veya kaynağının bulunduğu sunucu isteği iletin.</span><span class="sxs-lookup"><span data-stu-id="b01b2-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="b01b2-105">Proxy'leri uzak sunuculara gönderilen isteklerin sayısını azaltarak ağ performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b01b2-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="b01b2-106">Proxy'leri kaynaklara erişimi kısıtlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b01b2-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="b01b2-107">Uyarlamalı proxy'leri</span><span class="sxs-lookup"><span data-stu-id="b01b2-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="b01b2-108">.NET Framework'teki proxy'leri iki çeşit olarak bulunur: Uyarlamalı ve statik.</span><span class="sxs-lookup"><span data-stu-id="b01b2-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="b01b2-109">Ağ yapılandırma değiştiğinde Uyarlamalı proxy'leri ayarlarına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b01b2-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="b01b2-110">Örneğin, bir dizüstü bilgisayar kullanıcı bir çevirmeli ağ bağlantısı başlarsa, Uyarlamalı proxy bu değişikliği algılar, bulmak ve kendi yeni yapılandırma komut dosyasını çalıştırın ve kendi ayarlarını uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="b01b2-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="b01b2-111">Uyarlamalı proxy'leri yapılandırma komut dosyası tarafından yapılandırılır (bkz [Otomatik Proxy algılama](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="b01b2-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="b01b2-112">Komut dosyasını bir dizi uygulama protokolleri ve her protokol için bir proxy oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b01b2-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="b01b2-113">Ağ ortamında değişiklikleri sistem proxy'leri yeni bir dizi kullanmanızı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="b01b2-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="b01b2-114">Bir ağ bağlantısı arıza ya da yeni bir ağ bağlantısı başlatıldı, sistem yeni ortamındaki yapılandırma komut dosyası, uygun kaynak bulmak ve yeni komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b01b2-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="b01b2-115">Kullanabileceğiniz `usesystemdefault` özniteliği [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) yapılandırma dosyanızda öğesi.</span><span class="sxs-lookup"><span data-stu-id="b01b2-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="b01b2-116">`usesystemdefault` Statik proxy ayarları (proxy adresi, atlama listesi ve yerel atlama) kullanıcı için Internet Explorer proxy ayarları okumalısınız olup olmadığını kontrol eder özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b01b2-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="b01b2-117">Bu değer ayarlanırsa `true`, Internet Explorer'dan statik proxy ayarları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b01b2-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="b01b2-118">Bu değer ise `false` veya ayarlanmadı, statik proxy ayarlarını yapılandırma dosyasında belirtilen ve Internet Explorer proxy ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b01b2-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="b01b2-119">Bu değer ayrıca ayarlanmalıdır `false` veya uyarlamalı proxy'leri etkinleştirilmesi ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="b01b2-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="b01b2-120">Aşağıdaki örnek tipik Uyarlamalı proxy yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b01b2-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="b01b2-121">Statik proxy'leri</span><span class="sxs-lookup"><span data-stu-id="b01b2-121">Static Proxies</span></span>  
 <span data-ttu-id="b01b2-122">Statik proxy'leri genellikle açıkça bir uygulama tarafından veya bir yapılandırma dosyası bir uygulama veya sistem tarafından çağrıldığında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b01b2-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="b01b2-123">Statik proxy'leri içinde topoloji, bir kurumsal ağa bağlı bir masaüstü bilgisayar gibi sık değişmeyen ağlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="b01b2-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="b01b2-124">Çeşitli seçenekler statik proxy nasıl çalıştığını denetler.</span><span class="sxs-lookup"><span data-stu-id="b01b2-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="b01b2-125">Şunları belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b01b2-125">You can specify the following:</span></span>  
  
-   <span data-ttu-id="b01b2-126">Proxy adresi.</span><span class="sxs-lookup"><span data-stu-id="b01b2-126">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="b01b2-127">Proxy yerel adresler için atlanmasına.</span><span class="sxs-lookup"><span data-stu-id="b01b2-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="b01b2-128">Proxy adresleri kümesini için atlanmasına.</span><span class="sxs-lookup"><span data-stu-id="b01b2-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="b01b2-129">Aşağıdaki tabloda statik bir proxy sunucu için yapılandırma seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b01b2-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="b01b2-130">Öznitelik, özellik veya yapılandırma dosyası ayarı</span><span class="sxs-lookup"><span data-stu-id="b01b2-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="b01b2-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b01b2-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="b01b2-132">`proxyaddress` Veya <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="b01b2-132">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="b01b2-133">Kullanılacak proxy adresi.</span><span class="sxs-lookup"><span data-stu-id="b01b2-133">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="b01b2-134">`bypassonlocal` Veya <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="b01b2-134">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="b01b2-135">Yerel adresler için proxy atlanır olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="b01b2-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="b01b2-136">`bypasslist` Veya <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="b01b2-136">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="b01b2-137">, Normal ifadelerle bir proxy atlama adresi açıklar.</span><span class="sxs-lookup"><span data-stu-id="b01b2-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="b01b2-138">(Proxy adresi atlama listesine ve yerel atlama) statik proxy ayarlarını gerekip gerekmediğini kullanıcı için Internet Explorer proxy ayarlarını okunmasına denetler.</span><span class="sxs-lookup"><span data-stu-id="b01b2-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="b01b2-139">Bu değer ayarlanırsa `true`, Internet Explorer'dan statik proxy ayarları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b01b2-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="b01b2-140">Bu değer ayarlandığında .NET Framework 2.0 `true`, Internet Explorer proxy ayarlarını yapılandırma dosyasındaki diğer proxy ayarları tarafından geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="b01b2-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="b01b2-141">.NET Framework 1.1, Internet Explorer proxy ayarlarını diğer proxy ayarlarını yapılandırma dosyasında geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="b01b2-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="b01b2-142">Bu değer ise `false` veya ayarlanmadı, statik proxy ayarlarını yapılandırma dosyasında belirtilen sonra Internet Explorer proxy ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b01b2-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="b01b2-143">Bu değer ayrıca ayarlanmalıdır `false` veya uyarlamalı proxy'leri etkinleştirilmesi ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="b01b2-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="b01b2-144">Aşağıdaki örnek bir genel statik proxy yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b01b2-144">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b01b2-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b01b2-145">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="b01b2-146">Otomatik Ara Sunucu Algılama</span><span class="sxs-lookup"><span data-stu-id="b01b2-146">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
