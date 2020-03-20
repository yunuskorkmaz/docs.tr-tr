---
title: Otomatik Ara Sunucu Algılama
ms.date: 03/30/2017
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
ms.openlocfilehash: 4c5bc9e0efb39032d388d141e8bccf3e520ebd45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180892"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="5aa4b-102">Otomatik Ara Sunucu Algılama</span><span class="sxs-lookup"><span data-stu-id="5aa4b-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="5aa4b-103">Otomatik proxy algılama, bir Web proxy sunucusunun sistem tarafından tanımlandığı ve istemci adına istek göndermek için kullanıldığı bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="5aa4b-104">Bu özellik, Web Proxy Otomatik Bulma (WPAD) olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="5aa4b-105">Otomatik proxy algılama etkinleştirildiğinde, sistem istek için kullanılabilecek proxy kümesini döndürmekten sorumlu bir proxy yapılandırma komut dosyası bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="5aa4b-106">Proxy yapılandırma komut dosyası bulunursa, proxy bilgileri, istek akışı veya örnek <xref:System.Net.WebProxy> kullanan bir istek için yanıt elde edildiğinde komut dosyası karşıdan yüklenir, derlenir ve yerel bilgisayarda çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="5aa4b-107">Otomatik proxy algılama <xref:System.Net.WebProxy> sınıf tarafından gerçekleştirilir ve istek düzeyi ayarları, yapılandırma dosyalarındaki ayarları ve Internet Explorer Yerel Alan Ağı **(LAN)** iletişim kutusu kullanılarak belirtilen ayarları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5aa4b-108">Internet Explorer ana menüsünden **Araçlar'ı** seçip **Internet Seçenekleri'ni**seçerek Internet Explorer **Yerel Alan Ağı (LAN) Ayarları** iletişim kutusunu görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="5aa4b-109">Ardından, **Bağlantılar** sekmesini seçin ve **LAN Ayarları'nı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="5aa4b-110">Otomatik proxy algılama etkinleştirildiğinde, <xref:System.Net.WebProxy> sınıf proxy yapılandırma komut dosyası bulmak için çalışır aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="5aa4b-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1. <span data-ttu-id="5aa4b-111">WinINet `InternetQueryOption` işlevi, En son Internet Explorer tarafından algılanan proxy yapılandırma komut dosyasını bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2. <span data-ttu-id="5aa4b-112">Komut dosyası bulunmazsa, <xref:System.Net.WebProxy> sınıf komut dosyasını bulmak için Dinamik Ana Bilgisayar Yapılandırma Protokolü'nü (DHCP) kullanır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="5aa4b-113">DHCP sunucusu, komut dosyasının konumu (ana bilgisayar adı) veya komut dosyasının tam URL'si ile yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3. <span data-ttu-id="5aa4b-114">DHCP WPAD ana bilgisayarını tanımlamazsa, DNS adı veya diğer adı olarak WPAD'li bir ana bilgisayar için sorgulanır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4. <span data-ttu-id="5aa4b-115">Ana bilgisayar tanımlanmamışsa ve bir proxy yapılandırma komut dosyasının konumu Internet Explorer LAN ayarları veya yapılandırma dosyası tarafından belirtilirse, bu konum kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5aa4b-116">NT Hizmeti olarak veya ASP.NET bir parçası olarak çalışan uygulamalar, çağıran kullanıcının Internet Explorer proxy sunucu ayarlarını (varsa) kullanır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="5aa4b-117">Bu ayarlar tüm hizmet uygulamaları için kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="5aa4b-118">Ekseksitler her biri konnektoid olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="5aa4b-119">Connectoid, ağ bağlantısı iletişim kutusundaki bir öğedir ve fiziksel ağ aygıtı (modem veya Ethernet kartı) veya sanal arabirim (ağ aygıtı üzerinde çalışan VPN bağlantısı gibi) olabilir.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="5aa4b-120">Bir bağ-ı değiştiğinde (örneğin, kablosuz bağlantı bir erişim noktasını değiştirdiğinde veya VPN etkinleştirildiğinde), proxy algılama algoritması yeniden çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="5aa4b-121">Varsayılan olarak, Internet Explorer proxy ayarları proxy algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="5aa4b-122">Uygulamanız etkileşimli olmayan bir hesap altında çalışıyorsa (IE proxy ayarlarını yapılandırmak için uygun bir yol olmadan) veya IE ayarlarını farklı proxy ayarları kullanmak istiyorsanız, [ \<varsayılan Proxy> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) ve [ \<proxy> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/proxy-element-network-settings.md) öğeleri tanımlanan bir yapılandırma dosyası oluşturarak proxy'nizi yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="5aa4b-123">Oluşturduğunuz istekler için, aşağıdaki kod örneğinde gösterildiği gibi, isteğinizle birlikte bir null <xref:System.Net.WebRequest.Proxy%2A> kullanarak istek düzeyinde otomatik proxy algılamasını devre dışı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="5aa4b-124">Proxy'si olmayan istekler, uygulama etki alanınızın varsayılan proxy'sini <xref:System.Net.WebRequest.DefaultWebProxy%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa4b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aa4b-125">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="5aa4b-126">\<system.Net> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="5aa4b-126">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
