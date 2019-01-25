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
# <a name="automatic-proxy-detection"></a>Otomatik Proxy algılama
Otomatik proxy algılama, bir Web proxy sunucusu sistem tarafından tanımlanan ve istemci adına istek göndermek için kullanılan bir işlemdir. Bu özellik Web Proxy Otomatik Bulma (WPAD) de denir. Otomatik proxy algılama etkinleştirildiğinde, istek için kullanılan proxy kümesini döndürmekten sorumlu bir proxy yapılandırma betiğini bulmak sistem çalışır. Proxy yapılandırma betiği bulunursa, betik indirilen, derlenmiş ve kullandığı bir istek için proxy bilgilerini, istek akışı veya yanıt alındığında yerel bilgisayarda çalıştırmak bir <xref:System.Net.WebProxy> örneği.  
  
 Otomatik proxy algılama tarafından gerçekleştirilir <xref:System.Net.WebProxy> sınıfı ve istek düzeyi ayarları, yapılandırma dosyalarındaki ayarlar ve Internet Explorer'ı kullanarak belirtilen ayarları dağıtabileceklerinizle **yerel alan ağı (LAN)** iletişim kutusu.  
  
> [!NOTE]
>  Internet Explorer'ı görüntüleyebilir **yerel alan ağı (LAN) ayarları** iletişim kutusunu seçerek **Araçları** Internet Explorer ana menü ve ardından seçerek **InternetSeçenekleri**. Ardından, **bağlantıları** sekmesine ve tıklayın **LAN Ayarları**.  
  
 Otomatik proxy algılama etkinleştirildiğinde <xref:System.Net.WebProxy> sınıfı çalışır gibi proxy yapılandırma betiğini bulmak:  
  
1.  WinINet `InternetQueryOption` işlevi en Internet Explorer'ın en son algılanan proxy yapılandırma betiğini bulmak için kullanılır.  
  
2.  Komut dosyası bulunamazsa <xref:System.Net.WebProxy> sınıfı betiğini bulmak için Dinamik Ana Bilgisayar Yapılandırma Protokolü (DHCP) kullanır. DHCP sunucusu konumu (ana bilgisayar adı) ile ya da komut veya komut dosyası için tam bir URL ile yanıt verebilirsiniz.  
  
3.  DHCP WPAD konak tanımlamıyorsa, DNS adını veya diğer ad olarak WPAD olan bir konak için sorgulanır.  
  
4.  Bu konum, konak tanımlanmaz ve Internet Explorer LAN Ayarları veya bir yapılandırma dosyası bir proxy yapılandırma betiği konumunu belirtilirse kullanılır.  
  
> [!NOTE]
>  ASP.NET bir parçası olarak veya bir NT hizmeti olarak çalışan uygulamalar Internet Explorer proxy sunucusu ayarlarını çağrılıyor kullanıcısı (varsa) kullanın. Bu ayarlar tüm hizmet uygulamaları için kullanılamıyor olabilir.  
  
 Proxy bağlantı başına temelinde yapılandırılır. Bir bağlantı ağ bağlantısı iletişim kutusunda bir öğe ve bir fiziksel ağ aygıtı (bir modem veya Ethernet kartı) veya bir sanal arabirim (örneğin, bir ağ cihaz üzerinde çalışan bir VPN bağlantısı için) olabilir. Bağlantı değişiklikleri değiştiğinde (bir erişim noktası veya bir VPN etkinleştirilmiş örnek bir kablosuz bağlantı), proxy algılama algoritması yeniden çalıştırın.  
  
 Varsayılan olarak, Internet Explorer proxy ayarlarının proxy algılamak için kullanılır. Uygulamanızın etkileşimli olmayan bir hesap (olmadan, IE proxy ayarlarını yapılandırmak için kullanışlı bir yol) altında çalışıyorsa veya IE ayarlarından farklı proxy ayarlarını kullanmak istiyorsanız, ilebiryapılandırmadosyasıoluşturarakArasunucunuzyapılandırabilirsiniz[ \<defaultProxy > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) ve [ \<proxy > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) tanımlanan öğe.  
  
 Oluşturduğunuz istekleri, otomatik proxy algılama talep düzeyinde bir null kullanarak devre dışı bırakabilirsiniz <xref:System.Net.WebRequest.Proxy%2A> aşağıdaki kod örneğinde gösterildiği gibi isteğinizle birlikte.  
  
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
  
 Bir ara sunucu olmayan istekleri kullanılabilir uygulama etki alanının varsayılan proxy kullanmak <xref:System.Net.WebRequest.DefaultWebProxy%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [\<system.Net > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
