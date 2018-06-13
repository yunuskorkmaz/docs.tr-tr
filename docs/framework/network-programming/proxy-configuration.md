---
title: Proxy yapılandırması
ms.date: 03/30/2017
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
ms.openlocfilehash: 41e1dcee90531de605b6bddc1eedc1c44235d8eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397539"
---
# <a name="proxy-configuration"></a><span data-ttu-id="88111-102">Proxy yapılandırması</span><span class="sxs-lookup"><span data-stu-id="88111-102">Proxy Configuration</span></span>
<span data-ttu-id="88111-103">Bir proxy sunucu kaynakları için istemci isteklerini işler.</span><span class="sxs-lookup"><span data-stu-id="88111-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="88111-104">Bir proxy, istenen kaynak, önbellekten döndürür veya kaynağının bulunduğu sunucu isteği iletin.</span><span class="sxs-lookup"><span data-stu-id="88111-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="88111-105">Proxy'leri uzak sunuculara gönderilen isteklerin sayısını azaltarak ağ performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="88111-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="88111-106">Proxy'leri kaynaklara erişimi kısıtlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88111-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="88111-107">Uyarlamalı proxy'leri</span><span class="sxs-lookup"><span data-stu-id="88111-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="88111-108">.NET Framework'teki proxy'leri iki çeşit olarak bulunur: Uyarlamalı ve statik.</span><span class="sxs-lookup"><span data-stu-id="88111-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="88111-109">Ağ yapılandırma değiştiğinde Uyarlamalı proxy'leri ayarlarına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88111-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="88111-110">Örneğin, bir dizüstü bilgisayar kullanıcı bir çevirmeli ağ bağlantısı başlarsa, Uyarlamalı proxy bu değişikliği algılar, bulmak ve kendi yeni yapılandırma komut dosyasını çalıştırın ve kendi ayarlarını uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="88111-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="88111-111">Uyarlamalı proxy'leri yapılandırma komut dosyası tarafından yapılandırılır (bkz [Otomatik Proxy algılama](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="88111-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="88111-112">Komut dosyasını bir dizi uygulama protokolleri ve her protokol için bir proxy oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88111-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="88111-113">Çeşitli seçenekler yapılandırma komut dosyası çalışma şeklini denetler.</span><span class="sxs-lookup"><span data-stu-id="88111-113">Several options control how the configuration script is run.</span></span> <span data-ttu-id="88111-114">Şunları belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="88111-114">You can specify the following:</span></span>  
  
-   <span data-ttu-id="88111-115">Ne sıklıkta yapılandırma komut dosyası karşıdan çalıştırın ve.</span><span class="sxs-lookup"><span data-stu-id="88111-115">How often the configuration script is downloaded and run.</span></span>  
  
-   <span data-ttu-id="88111-116">Karşıdan yüklemek komut dosyası için beklenecek süreyi.</span><span class="sxs-lookup"><span data-stu-id="88111-116">How long to wait for the script to download.</span></span>  
  
-   <span data-ttu-id="88111-117">Hangi sisteminizi kimlik bilgileri proxy sunucusuna erişmek için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="88111-117">Which credentials your system should use to access the proxy.</span></span>  
  
-   <span data-ttu-id="88111-118">Hangi sisteminizi kimlik bilgileri yapılandırma betiğini indir için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="88111-118">Which credentials your system should use to download the configuration script.</span></span>  
  
 <span data-ttu-id="88111-119">Ağ ortamında değişiklikleri sistem proxy'leri yeni bir dizi kullanmanızı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="88111-119">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="88111-120">Bir ağ bağlantısı arıza ya da yeni bir ağ bağlantısı başlatıldı, sistem yeni ortamındaki yapılandırma komut dosyası, uygun kaynak bulmak ve yeni komut dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="88111-120">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="88111-121">Aşağıdaki tabloda, Uyarlamalı proxy için yapılandırma seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="88111-121">The following table shows configuration options for an adaptive proxy.</span></span>  
  
|<span data-ttu-id="88111-122">Öznitelik, özellik veya yapılandırma dosyası ayarı</span><span class="sxs-lookup"><span data-stu-id="88111-122">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="88111-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88111-123">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|<span data-ttu-id="88111-124">Komut dosyası indirmeler arasındaki saniye cinsinden geçen süre.</span><span class="sxs-lookup"><span data-stu-id="88111-124">Elapsed time in seconds between script downloads.</span></span>|  
|`scriptDownloadTimeout`|<span data-ttu-id="88111-125">(Saniye cinsinden) indirmek komut dosyası için beklenecek süre.</span><span class="sxs-lookup"><span data-stu-id="88111-125">Time to wait (in seconds) for the script to download.</span></span>|  
|<span data-ttu-id="88111-126">`useDefaultCredentials` Veya <xref:System.Net.WebProxy.UseDefaultCredentials></span><span class="sxs-lookup"><span data-stu-id="88111-126">`useDefaultCredentials` or <xref:System.Net.WebProxy.UseDefaultCredentials></span></span>|<span data-ttu-id="88111-127">Sistem bir proxy sunucusuna erişmek için varsayılan ağ kimlik bilgilerini kullanıp kullanmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="88111-127">Controls whether the system uses the default network credentials to access a proxy.</span></span>|  
|`useDefaultCredentialForScriptDownload`|<span data-ttu-id="88111-128">Sistem yapılandırma komut dosyasını indirmek için varsayılan ağ kimlik bilgilerini kullanıp kullanmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="88111-128">Controls whether the system uses the default network credentials to download the configuration script.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="88111-129">(Proxy adresi atlama listesine ve yerel atlama) statik proxy ayarlarını gerekip gerekmediğini kullanıcı için Internet Explorer proxy ayarlarını okunmasına denetler.</span><span class="sxs-lookup"><span data-stu-id="88111-129">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="88111-130">Bu değer "true", sonra statik proxy ayarlarını Internet Explorer'dan ayarlanmışsa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88111-130">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span><br /><br /> <span data-ttu-id="88111-131">Bu değer ise "false" veya değil kümesi ve statik proxy ayarlarını yapılandırmada belirtilen ve Internet Explorer proxy ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="88111-131">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="88111-132">Bu değer ayrıca "false" veya etkinleştirilecek Uyarlamalı proxy'leri için ayarlanmadı ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="88111-132">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="88111-133">Aşağıdaki örnek tipik Uyarlamalı proxy yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88111-133">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="88111-134">Statik proxy'leri</span><span class="sxs-lookup"><span data-stu-id="88111-134">Static Proxies</span></span>  
 <span data-ttu-id="88111-135">Statik proxy'leri genellikle açıkça bir uygulama tarafından veya bir yapılandırma dosyası bir uygulama veya sistem tarafından çağrıldığında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="88111-135">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="88111-136">Statik proxy'leri içinde topoloji, bir kurumsal ağa bağlı bir masaüstü bilgisayar gibi sık değişmeyen ağlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="88111-136">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="88111-137">Çeşitli seçenekler statik proxy nasıl çalıştığını denetler.</span><span class="sxs-lookup"><span data-stu-id="88111-137">Several options control how a static proxy operates.</span></span> <span data-ttu-id="88111-138">Şunları belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="88111-138">You can specify the following:</span></span>  
  
-   <span data-ttu-id="88111-139">Proxy adresi.</span><span class="sxs-lookup"><span data-stu-id="88111-139">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="88111-140">Proxy yerel adresler için atlanmasına.</span><span class="sxs-lookup"><span data-stu-id="88111-140">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="88111-141">Proxy adresleri kümesini için atlanmasına.</span><span class="sxs-lookup"><span data-stu-id="88111-141">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="88111-142">Aşağıdaki tabloda statik bir proxy sunucu için yapılandırma seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="88111-142">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="88111-143">Öznitelik, özellik veya yapılandırma dosyası ayarı</span><span class="sxs-lookup"><span data-stu-id="88111-143">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="88111-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88111-144">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="88111-145">`proxyaddress` Veya <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="88111-145">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="88111-146">Kullanılacak proxy adresi.</span><span class="sxs-lookup"><span data-stu-id="88111-146">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="88111-147">`bypassonlocal` Veya <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="88111-147">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="88111-148">Yerel adresler için proxy atlanır olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="88111-148">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="88111-149">`bypasslist` Veya <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="88111-149">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="88111-150">, Normal ifadelerle bir proxy atlama adresi açıklar.</span><span class="sxs-lookup"><span data-stu-id="88111-150">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="88111-151">(Proxy adresi atlama listesine ve yerel atlama) statik proxy ayarlarını gerekip gerekmediğini kullanıcı için Internet Explorer proxy ayarlarını okunmasına denetler.</span><span class="sxs-lookup"><span data-stu-id="88111-151">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="88111-152">Bu değer "true", sonra statik proxy ayarlarını Internet Explorer'dan ayarlanmışsa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88111-152">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="88111-153">.NET Framework bu değer "true", Internet Explorer proxy ayarları diğer proxy ayarlarını yapılandırma dosyasındaki tarafından geçersiz kılınmaz ayarlandığında 2.0.</span><span class="sxs-lookup"><span data-stu-id="88111-153">On .NET Framework 2.0 when this value is set to "true", the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="88111-154">.NET Framework 1.1, Internet Explorer proxy ayarlarını diğer proxy ayarlarını yapılandırma dosyasında geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="88111-154">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="88111-155">Bu değer ise "false" veya değil kümesi ve statik proxy ayarlarını yapılandırmada belirtilen ve Internet Explorer proxy ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="88111-155">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="88111-156">Bu değer ayrıca "false" veya etkinleştirilecek Uyarlamalı proxy'leri için ayarlanmadı ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="88111-156">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="88111-157">Aşağıdaki örnek bir genel statik proxy yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88111-157">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88111-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88111-158">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="88111-159">Otomatik Ara Sunucu Algılama</span><span class="sxs-lookup"><span data-stu-id="88111-159">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
