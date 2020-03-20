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
# <a name="automatic-proxy-detection"></a>Otomatik Ara Sunucu Algılama
Otomatik proxy algılama, bir Web proxy sunucusunun sistem tarafından tanımlandığı ve istemci adına istek göndermek için kullanıldığı bir işlemdir. Bu özellik, Web Proxy Otomatik Bulma (WPAD) olarak da bilinir. Otomatik proxy algılama etkinleştirildiğinde, sistem istek için kullanılabilecek proxy kümesini döndürmekten sorumlu bir proxy yapılandırma komut dosyası bulmaya çalışır. Proxy yapılandırma komut dosyası bulunursa, proxy bilgileri, istek akışı veya örnek <xref:System.Net.WebProxy> kullanan bir istek için yanıt elde edildiğinde komut dosyası karşıdan yüklenir, derlenir ve yerel bilgisayarda çalıştırılır.  
  
 Otomatik proxy algılama <xref:System.Net.WebProxy> sınıf tarafından gerçekleştirilir ve istek düzeyi ayarları, yapılandırma dosyalarındaki ayarları ve Internet Explorer Yerel Alan Ağı **(LAN)** iletişim kutusu kullanılarak belirtilen ayarları kullanabilir.  
  
> [!NOTE]
> Internet Explorer ana menüsünden **Araçlar'ı** seçip **Internet Seçenekleri'ni**seçerek Internet Explorer **Yerel Alan Ağı (LAN) Ayarları** iletişim kutusunu görüntüleyebilirsiniz. Ardından, **Bağlantılar** sekmesini seçin ve **LAN Ayarları'nı**tıklatın.  
  
 Otomatik proxy algılama etkinleştirildiğinde, <xref:System.Net.WebProxy> sınıf proxy yapılandırma komut dosyası bulmak için çalışır aşağıdaki gibi:  
  
1. WinINet `InternetQueryOption` işlevi, En son Internet Explorer tarafından algılanan proxy yapılandırma komut dosyasını bulmak için kullanılır.  
  
2. Komut dosyası bulunmazsa, <xref:System.Net.WebProxy> sınıf komut dosyasını bulmak için Dinamik Ana Bilgisayar Yapılandırma Protokolü'nü (DHCP) kullanır. DHCP sunucusu, komut dosyasının konumu (ana bilgisayar adı) veya komut dosyasının tam URL'si ile yanıt verebilir.  
  
3. DHCP WPAD ana bilgisayarını tanımlamazsa, DNS adı veya diğer adı olarak WPAD'li bir ana bilgisayar için sorgulanır.  
  
4. Ana bilgisayar tanımlanmamışsa ve bir proxy yapılandırma komut dosyasının konumu Internet Explorer LAN ayarları veya yapılandırma dosyası tarafından belirtilirse, bu konum kullanılır.  
  
> [!NOTE]
> NT Hizmeti olarak veya ASP.NET bir parçası olarak çalışan uygulamalar, çağıran kullanıcının Internet Explorer proxy sunucu ayarlarını (varsa) kullanır. Bu ayarlar tüm hizmet uygulamaları için kullanılamayabilir.  
  
 Ekseksitler her biri konnektoid olarak yapılandırılır. Connectoid, ağ bağlantısı iletişim kutusundaki bir öğedir ve fiziksel ağ aygıtı (modem veya Ethernet kartı) veya sanal arabirim (ağ aygıtı üzerinde çalışan VPN bağlantısı gibi) olabilir. Bir bağ-ı değiştiğinde (örneğin, kablosuz bağlantı bir erişim noktasını değiştirdiğinde veya VPN etkinleştirildiğinde), proxy algılama algoritması yeniden çalıştırılır.  
  
 Varsayılan olarak, Internet Explorer proxy ayarları proxy algılamak için kullanılır. Uygulamanız etkileşimli olmayan bir hesap altında çalışıyorsa (IE proxy ayarlarını yapılandırmak için uygun bir yol olmadan) veya IE ayarlarını farklı proxy ayarları kullanmak istiyorsanız, [ \<varsayılan Proxy> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) ve [ \<proxy> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/proxy-element-network-settings.md) öğeleri tanımlanan bir yapılandırma dosyası oluşturarak proxy'nizi yapılandırabilirsiniz.  
  
 Oluşturduğunuz istekler için, aşağıdaki kod örneğinde gösterildiği gibi, isteğinizle birlikte bir null <xref:System.Net.WebRequest.Proxy%2A> kullanarak istek düzeyinde otomatik proxy algılamasını devre dışı kullanabilirsiniz.  
  
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
  
 Proxy'si olmayan istekler, uygulama etki alanınızın varsayılan proxy'sini <xref:System.Net.WebRequest.DefaultWebProxy%2A> kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [\<system.Net> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
