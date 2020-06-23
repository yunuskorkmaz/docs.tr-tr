---
title: Ara Sunucu Yapılandırma
description: Uyarlamalı ve statik proxy sunucularının nasıl yapılandırılacağı hakkında bilgi edinin. Proxy yapılandırması, bir proxy sunucusunun kaynaklar için istemci isteklerini nasıl işlediğini denetler.
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
ms.openlocfilehash: 4d62f5736e9aa469be49d101e85851bc01b7c159
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141611"
---
# <a name="proxy-configuration"></a><span data-ttu-id="9f07a-104">Ara Sunucu Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f07a-104">Proxy Configuration</span></span>
<span data-ttu-id="9f07a-105">Proxy sunucusu, kaynaklar için istemci isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="9f07a-105">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="9f07a-106">Bir ara sunucu, önbelleğinden istenen bir kaynağı döndürebilir veya isteği kaynağın bulunduğu sunucuya iletebilir.</span><span class="sxs-lookup"><span data-stu-id="9f07a-106">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="9f07a-107">Proxy 'ler, uzak sunuculara gönderilen isteklerin sayısını azaltarak ağ performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="9f07a-107">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="9f07a-108">Proxy 'ler, kaynaklara erişimi kısıtlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f07a-108">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="9f07a-109">Uyarlamalı proxy 'Ler</span><span class="sxs-lookup"><span data-stu-id="9f07a-109">Adaptive Proxies</span></span>  
 <span data-ttu-id="9f07a-110">.NET Framework, proxy 'ler iki değişken halinde gelir: Uyarlamalı ve statik.</span><span class="sxs-lookup"><span data-stu-id="9f07a-110">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="9f07a-111">Uyarlamalı proxy 'ler, ağ yapılandırması değiştiğinde ayarlarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9f07a-111">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="9f07a-112">Örneğin, bir dizüstü Kullanıcı Çevirmeli ağ bağlantısı başlattığında, bir uyarlamalı ara sunucu bu değişikliği algılar, yeni yapılandırma betiğini bulur ve çalıştırır ve ayarlarını uygun şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9f07a-112">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="9f07a-113">Uyarlamalı proxy 'ler bir yapılandırma betiği tarafından yapılandırılır (bkz. [otomatik proxy algılama](automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="9f07a-113">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="9f07a-114">Betik, her protokol için bir dizi uygulama protokolü ve ara sunucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f07a-114">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="9f07a-115">Ağ ortamındaki değişiklikler sistemin yeni bir proxy kümesi kullanmasını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="9f07a-115">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="9f07a-116">Bir ağ bağlantısı kapalıysa veya yeni bir ağ bağlantısı başlatılmışsa, sistem yeni ortamda yapılandırma betiğinin uygun kaynağını bulmalı ve yeni betiği çalıştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f07a-116">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="9f07a-117">`usesystemdefault` [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) Yapılandırma dosyanızda öğesinin özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f07a-117">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="9f07a-118">`usesystemdefault`Özniteliği, statik ara sunucu ayarlarının (proxy adresi, atlama listesi ve yerel üzerinde atlama) Kullanıcı Için Internet Explorer proxy ayarlarından okunmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="9f07a-118">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="9f07a-119">Bu değer olarak ayarlanırsa `true` , Internet Explorer 'daki statik proxy ayarları kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="9f07a-119">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="9f07a-120">Bu değer `false` ayarlanmamışsa, yapılandırmada statik ara sunucu ayarları belirtilebilir ve Internet Explorer ara sunucu ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9f07a-120">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="9f07a-121">Bu değer Ayrıca, `false` Uyarlamalı proxy 'lerin etkinleştirilmesi için olarak ayarlanmalıdır veya ayarlanmamış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f07a-121">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="9f07a-122">Aşağıdaki örnek, tipik bir uyarlamalı ara sunucu yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f07a-122">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="9f07a-123">Statik proxy 'Ler</span><span class="sxs-lookup"><span data-stu-id="9f07a-123">Static Proxies</span></span>  
 <span data-ttu-id="9f07a-124">Statik proxy 'ler genellikle bir uygulama tarafından açıkça veya bir yapılandırma dosyası bir uygulama veya sistem tarafından çağrıldığında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="9f07a-124">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="9f07a-125">Statik proxy 'ler, bir kurumsal ağa bağlı bir masaüstü bilgisayar gibi, topolojinin seyrek değiştiği ağlarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9f07a-125">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="9f07a-126">Statik bir proxy 'nin nasıl çalıştığını çeşitli seçenekler denetler.</span><span class="sxs-lookup"><span data-stu-id="9f07a-126">Several options control how a static proxy operates.</span></span> <span data-ttu-id="9f07a-127">Aşağıdakileri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9f07a-127">You can specify the following:</span></span>  
  
- <span data-ttu-id="9f07a-128">Proxy adresi.</span><span class="sxs-lookup"><span data-stu-id="9f07a-128">The address of the proxy.</span></span>  
  
- <span data-ttu-id="9f07a-129">Yerel adresler için proxy 'nin atlanıp atlanmayacağı.</span><span class="sxs-lookup"><span data-stu-id="9f07a-129">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="9f07a-130">Bir adres kümesi için proxy 'nin atlanıp atlanmayacağı.</span><span class="sxs-lookup"><span data-stu-id="9f07a-130">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="9f07a-131">Aşağıdaki tabloda bir statik ara sunucu için yapılandırma seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9f07a-131">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="9f07a-132">Öznitelik, özellik veya yapılandırma dosyası ayarı</span><span class="sxs-lookup"><span data-stu-id="9f07a-132">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="9f07a-133">Description</span><span class="sxs-lookup"><span data-stu-id="9f07a-133">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="9f07a-134">`proxyaddress` veya <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="9f07a-134">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="9f07a-135">Kullanılacak proxy 'nin adresi.</span><span class="sxs-lookup"><span data-stu-id="9f07a-135">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="9f07a-136">`bypassonlocal` veya <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="9f07a-136">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="9f07a-137">Yerel adresler için proxy 'nin atlanıp atlanmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="9f07a-137">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="9f07a-138">`bypasslist` veya <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="9f07a-138">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="9f07a-139">Normal ifadelerle, proxy 'yi atlayan bir adres kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9f07a-139">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="9f07a-140">Statik ara sunucu ayarlarının (proxy adresi, atlama listesi ve yerel üzerinde atlama) Kullanıcı için Internet Explorer proxy ayarlarından okunmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="9f07a-140">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="9f07a-141">Bu değer olarak ayarlanırsa `true` , Internet Explorer 'daki statik proxy ayarları kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="9f07a-141">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="9f07a-142">.NET Framework 2,0 ' de, bu değer olarak ayarlandığında `true` , Internet Explorer proxy ayarları yapılandırma dosyasındaki diğer proxy ayarları tarafından geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="9f07a-142">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="9f07a-143">.NET Framework 1,1 ' de, Internet Explorer proxy ayarları yapılandırma dosyasındaki diğer proxy ayarları tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="9f07a-143">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="9f07a-144">Bu değer `false` ayarlanmamışsa, yapılandırmada statik ara sunucu ayarları belirtilebilir ve Internet Explorer ara sunucu ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9f07a-144">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="9f07a-145">Bu değer Ayrıca, `false` Uyarlamalı proxy 'lerin etkinleştirilmesi için olarak ayarlanmalıdır veya ayarlanmamış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f07a-145">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="9f07a-146">Aşağıdaki örnek, tipik bir statik ara sunucu yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f07a-146">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="True"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f07a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f07a-147">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="9f07a-148">Otomatik Ara Sunucu Algılama</span><span class="sxs-lookup"><span data-stu-id="9f07a-148">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
