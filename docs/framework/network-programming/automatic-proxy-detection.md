---
title: Otomatik Proxy algılama
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
ms.openlocfilehash: 5f79f25e879df85fed7b6e402d47d98f047dd562
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699863"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="d0f60-102">Otomatik Proxy algılama</span><span class="sxs-lookup"><span data-stu-id="d0f60-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="d0f60-103">Otomatik proxy algılama, bir Web proxy sunucusu sistem tarafından tanımlanan ve istemci adına istek göndermek için kullanılan bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="d0f60-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="d0f60-104">Bu özellik Web Proxy Otomatik Bulma (WPAD) de denir.</span><span class="sxs-lookup"><span data-stu-id="d0f60-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="d0f60-105">Otomatik proxy algılama etkinleştirildiğinde, istek için kullanılan proxy kümesini döndürmekten sorumlu bir proxy yapılandırma betiğini bulmak sistem çalışır.</span><span class="sxs-lookup"><span data-stu-id="d0f60-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="d0f60-106">Proxy yapılandırma betiği bulunursa, betik indirilen, derlenmiş ve kullandığı bir istek için proxy bilgilerini, istek akışı veya yanıt alındığında yerel bilgisayarda çalıştırmak bir <xref:System.Net.WebProxy> örneği.</span><span class="sxs-lookup"><span data-stu-id="d0f60-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="d0f60-107">Otomatik proxy algılama tarafından gerçekleştirilir <xref:System.Net.WebProxy> sınıfı ve istek düzeyi ayarları, yapılandırma dosyalarındaki ayarlar ve Internet Explorer'ı kullanarak belirtilen ayarları dağıtabileceklerinizle **yerel alan ağı (LAN)** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d0f60-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0f60-108">Internet Explorer'ı görüntüleyebilir **yerel alan ağı (LAN) ayarları** iletişim kutusunu seçerek **Araçları** Internet Explorer ana menü ve ardından seçerek **InternetSeçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="d0f60-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="d0f60-109">Ardından, **bağlantıları** sekmesine ve tıklayın **LAN Ayarları**.</span><span class="sxs-lookup"><span data-stu-id="d0f60-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="d0f60-110">Otomatik proxy algılama etkinleştirildiğinde <xref:System.Net.WebProxy> sınıfı çalışır gibi proxy yapılandırma betiğini bulmak:</span><span class="sxs-lookup"><span data-stu-id="d0f60-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1.  <span data-ttu-id="d0f60-111">WinINet `InternetQueryOption` işlevi en Internet Explorer'ın en son algılanan proxy yapılandırma betiğini bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0f60-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="d0f60-112">Komut dosyası bulunamazsa <xref:System.Net.WebProxy> sınıfı betiğini bulmak için Dinamik Ana Bilgisayar Yapılandırma Protokolü (DHCP) kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0f60-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="d0f60-113">DHCP sunucusu konumu (ana bilgisayar adı) ile ya da komut veya komut dosyası için tam bir URL ile yanıt verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0f60-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3.  <span data-ttu-id="d0f60-114">DHCP WPAD konak tanımlamıyorsa, DNS adını veya diğer ad olarak WPAD olan bir konak için sorgulanır.</span><span class="sxs-lookup"><span data-stu-id="d0f60-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4.  <span data-ttu-id="d0f60-115">Bu konum, konak tanımlanmaz ve Internet Explorer LAN Ayarları veya bir yapılandırma dosyası bir proxy yapılandırma betiği konumunu belirtilirse kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0f60-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0f60-116">ASP.NET bir parçası olarak veya bir NT hizmeti olarak çalışan uygulamalar Internet Explorer proxy sunucusu ayarlarını çağrılıyor kullanıcısı (varsa) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0f60-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="d0f60-117">Bu ayarlar tüm hizmet uygulamaları için kullanılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0f60-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="d0f60-118">Proxy bağlantı başına temelinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="d0f60-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="d0f60-119">Bir bağlantı ağ bağlantısı iletişim kutusunda bir öğe ve bir fiziksel ağ aygıtı (bir modem veya Ethernet kartı) veya bir sanal arabirim (örneğin, bir ağ cihaz üzerinde çalışan bir VPN bağlantısı için) olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0f60-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="d0f60-120">Bağlantı değişiklikleri değiştiğinde (bir erişim noktası veya bir VPN etkinleştirilmiş örnek bir kablosuz bağlantı), proxy algılama algoritması yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d0f60-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="d0f60-121">Varsayılan olarak, Internet Explorer proxy ayarlarının proxy algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0f60-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="d0f60-122">Uygulamanızın etkileşimli olmayan bir hesap (olmadan, IE proxy ayarlarını yapılandırmak için kullanışlı bir yol) altında çalışıyorsa veya IE ayarlarından farklı proxy ayarlarını kullanmak istiyorsanız, ilebiryapılandırmadosyasıoluşturarakArasunucunuzyapılandırabilirsiniz[ \<defaultProxy > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) ve [ \<proxy > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) tanımlanan öğe.</span><span class="sxs-lookup"><span data-stu-id="d0f60-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="d0f60-123">Oluşturduğunuz istekleri, otomatik proxy algılama talep düzeyinde bir null kullanarak devre dışı bırakabilirsiniz <xref:System.Net.WebRequest.Proxy%2A> aşağıdaki kod örneğinde gösterildiği gibi isteğinizle birlikte.</span><span class="sxs-lookup"><span data-stu-id="d0f60-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="d0f60-124">Bir ara sunucu olmayan istekleri kullanılabilir uygulama etki alanının varsayılan proxy kullanmak <xref:System.Net.WebRequest.DefaultWebProxy%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d0f60-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f60-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0f60-125">See also</span></span>
- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="d0f60-126">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="d0f60-126">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
