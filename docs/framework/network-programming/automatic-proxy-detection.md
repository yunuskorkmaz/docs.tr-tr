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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: acb14d8785a01d98d56233b8eb942f9bc4675f63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394887"
---
# <a name="automatic-proxy-detection"></a>Otomatik Proxy algılama
Otomatik proxy algılama olarak bir Web proxy sunucusu sistem tarafından tanımlanan ve istemci adına istekleri göndermek için kullanılan bir işlemdir. Bu özellik Web Proxy Otomatik Bulma (WPAD) de denir. Otomatik proxy algılaması etkinleştirildiğinde, sistem istek için kullanılan proxy kümesi döndürmek için sorumlu olduğu bir proxy yapılandırması komut dosyası bulmaya çalışır. Proxy yapılandırması komut dosyası bulunursa, komut dosyasını karşıdan derlenmiş ve kullanan bir istek için proxy bilgileri, istek akışı veya yanıtı alındığında yerel bilgisayarda çalıştırmak bir <xref:System.Net.WebProxy> örneği.  
  
 Otomatik proxy algılama tarafından gerçekleştirilir <xref:System.Net.WebProxy> sınıfı ve istek düzeyi ayarları, yapılandırma dosyalarında ayarlar ve Internet Explorer'ı kullanarak belirtilen ayarları uygulayabileceğiniz **yerel ağ (LAN)** iletişim kutusu.  
  
> [!NOTE]
>  Internet Explorer görüntüleyebilir **yerel ağ (LAN) ayarları** seçerek iletişim kutusu **Araçları** Internet Explorer ana menü ve ardından seçme **Internet Seçenekleri**. Ardından, **bağlantıları** sekmesine ve tıklayın **LAN Ayarları**.  
  
 Otomatik proxy algılama etkin olduğunda, <xref:System.Net.WebProxy> sınıfı çalışır proxy yapılandırma betiği aşağıdaki gibi bulmak:  
  
1.  WinINet `InternetQueryOption` işlevi, Internet Explorer'ın en son algılanan en proxy yapılandırma betiğini bulmak için kullanılır.  
  
2.  Komut dosyası bulunamazsa, <xref:System.Net.WebProxy> sınıfı betiğini bulmak için Dinamik Ana Bilgisayar Yapılandırma Protokolü (DHCP) kullanır. DHCP sunucusu konumu (ana bilgisayar adı) ile ya da komut dosyasının veya komut dosyası için tam bir URL ile yanıt verebilir.  
  
3.  DHCP WPAD konak tanımlamıyorsa, DNS WPAD ile ana bilgisayar adını veya diğer ad olarak için sorgulanır.  
  
4.  Konak tanımlanmadığı ve Internet Explorer LAN Ayarları veya bir yapılandırma dosyası bir proxy yapılandırması komut dosyası konumunu belirtilirse, bu konum kullanılır.  
  
> [!NOTE]
>  ASP.NET bir parçası olarak veya bir NT hizmeti olarak çalışan uygulamalar, Internet Explorer proxy sunucusu ayarları (varsa)'yi bildirilecekse kullanıcısı kullanın. Bu ayarlar tüm hizmet uygulamaları için kullanılamayabilir.  
  
 Proxy'leri bir bağlantı başına temelinde yapılandırılır. Bir bağlantı ağ bağlantısı iletişim kutusunda bir öğe ve bir fiziksel ağ aygıtı (modem veya Ethernet kartı) ya da sanal bir arabirim (örneğin, bir ağ aygıtı çalışan bir VPN bağlantısı için) olabilir. Bağlantı değişiklikleri değiştiğinde (bir erişim noktası veya bir VPN etkin Örneğin, bir kablosuz bağlantı), proxy algılama algoritması yeniden çalıştırın.  
  
 Varsayılan olarak, Internet Explorer proxy ayarlarını proxy algılama için kullanılır. Uygulamanız (olmadan IE proxy ayarlarını yapılandırmak için kolay bir yol) etkileşimli olmayan bir hesabı altında çalışıyorsa, veya IE ayarlarından farklı proxy ayarlarını kullanmak istiyorsanız, ilebiryapılandırmadosyasıoluşturarakproxyyapılandırabilirsiniz[ \<defaultProxy > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) ve [ \<proxy > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) öğesi tanımlandı.  
  
 Oluşturduğunuz istekleri için otomatik proxy algılama isteği düzeyinde null kullanarak devre dışı bırakabilirsiniz <xref:System.Net.WebRequest.Proxy%2A> aşağıdaki kod örneğinde gösterildiği gibi istek ile.  
  
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
  
 Bir proxy olmayan istekleri kullanır kullanılabilir uygulama etki alanınızın varsayılan proxy <xref:System.Net.WebRequest.DefaultWebProxy%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [\<system.Net > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
