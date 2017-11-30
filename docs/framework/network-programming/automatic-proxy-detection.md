---
title: "Otomatik Proxy algılama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8eec6ff84978cdbd31dd4be307d0eb9560edde19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="ecb5e-102">Otomatik Proxy algılama</span><span class="sxs-lookup"><span data-stu-id="ecb5e-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="ecb5e-103">Otomatik proxy algılama olarak bir Web proxy sunucusu sistem tarafından tanımlanan ve istemci adına istekleri göndermek için kullanılan bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="ecb5e-104">Bu özellik Web Proxy Otomatik Bulma (WPAD) de denir.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="ecb5e-105">Otomatik proxy algılaması etkinleştirildiğinde, sistem istek için kullanılan proxy kümesi döndürmek için sorumlu olduğu bir proxy yapılandırması komut dosyası bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="ecb5e-106">Proxy yapılandırması komut dosyası bulunursa, komut dosyasını karşıdan derlenmiş ve kullanan bir istek için proxy bilgileri, istek akışı veya yanıtı alındığında yerel bilgisayarda çalıştırmak bir <xref:System.Net.WebProxy> örneği.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="ecb5e-107">Otomatik proxy algılama tarafından gerçekleştirilir <xref:System.Net.WebProxy> sınıfı ve istek düzeyi ayarları, yapılandırma dosyalarında ayarlar ve Internet Explorer'ı kullanarak belirtilen ayarları uygulayabileceğiniz **yerel ağ (LAN)** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecb5e-108">Internet Explorer görüntüleyebilir **yerel ağ (LAN) ayarları** seçerek iletişim kutusu **Araçları** Internet Explorer ana menü ve ardından seçme **Internet Seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="ecb5e-109">Ardından, **bağlantıları** sekmesine ve tıklayın **LAN Ayarları**.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="ecb5e-110">Otomatik proxy algılama etkin olduğunda, <xref:System.Net.WebProxy> sınıfı çalışır proxy yapılandırma betiği aşağıdaki gibi bulmak:</span><span class="sxs-lookup"><span data-stu-id="ecb5e-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1.  <span data-ttu-id="ecb5e-111">WinINet `InternetQueryOption` işlevi, Internet Explorer'ın en son algılanan en proxy yapılandırma betiğini bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="ecb5e-112">Komut dosyası bulunamazsa, <xref:System.Net.WebProxy> sınıfı betiğini bulmak için Dinamik Ana Bilgisayar Yapılandırma Protokolü (DHCP) kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="ecb5e-113">DHCP sunucusu konumu (ana bilgisayar adı) ile ya da komut dosyasının veya komut dosyası için tam bir URL ile yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3.  <span data-ttu-id="ecb5e-114">DHCP WPAD konak tanımlamıyorsa, DNS WPAD ile ana bilgisayar adını veya diğer ad olarak için sorgulanır.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4.  <span data-ttu-id="ecb5e-115">Konak tanımlanmadığı ve Internet Explorer LAN Ayarları veya bir yapılandırma dosyası bir proxy yapılandırması komut dosyası konumunu belirtilirse, bu konum kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecb5e-116">ASP.NET bir parçası olarak veya bir NT hizmeti olarak çalışan uygulamalar, Internet Explorer proxy sunucusu ayarları (varsa)'yi bildirilecekse kullanıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="ecb5e-117">Bu ayarlar tüm hizmet uygulamaları için kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="ecb5e-118">Proxy'leri bir bağlantı başına temelinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="ecb5e-119">Bir bağlantı ağ bağlantısı iletişim kutusunda bir öğe ve bir fiziksel ağ aygıtı (modem veya Ethernet kartı) ya da sanal bir arabirim (örneğin, bir ağ aygıtı çalışan bir VPN bağlantısı için) olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="ecb5e-120">Bağlantı değişiklikleri değiştiğinde (bir erişim noktası veya bir VPN etkin Örneğin, bir kablosuz bağlantı), proxy algılama algoritması yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="ecb5e-121">Varsayılan olarak, Internet Explorer proxy ayarlarını proxy algılama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="ecb5e-122">Uygulamanız (olmadan IE proxy ayarlarını yapılandırmak için kolay bir yol) etkileşimli olmayan bir hesabı altında çalışıyorsa, veya IE ayarlarından farklı proxy ayarlarını kullanmak istiyorsanız, ilebiryapılandırmadosyasıoluşturarakproxyyapılandırabilirsiniz[ \<defaultProxy > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) ve [ \<proxy > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) öğesi tanımlandı.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="ecb5e-123">Oluşturduğunuz istekleri için otomatik proxy algılama isteği düzeyinde null kullanarak devre dışı bırakabilirsiniz <xref:System.Net.WebRequest.Proxy%2A> aşağıdaki kod örneğinde gösterildiği gibi istek ile.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub   
```  
  
 <span data-ttu-id="ecb5e-124">Bir proxy olmayan istekleri kullanır kullanılabilir uygulama etki alanınızın varsayılan proxy <xref:System.Net.WebRequest.DefaultWebProxy%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb5e-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ecb5e-125">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="ecb5e-126">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="ecb5e-126">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
