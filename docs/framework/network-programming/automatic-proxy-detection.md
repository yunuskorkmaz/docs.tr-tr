---
title: Otomatik Ara Sunucu Algılama
description: Sistemin bir Web proxy sunucusu tanımladığı ve istemci adına istek göndermek için kullandığı otomatik proxy algılaması hakkında bilgi edinin.
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
ms.openlocfilehash: dbd5d7fa671ae5ec3b7dc00205f0c9d8381bb3ce
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502709"
---
# <a name="automatic-proxy-detection"></a>Otomatik Ara Sunucu Algılama
Otomatik proxy algılama, sistem tarafından bir Web proxy sunucusunun tanımlandığı ve istemci adına istek göndermek için kullanılan bir işlemdir. Bu özellik Web proxy otomatik bulma (WPAD) olarak da bilinir. Otomatik ara sunucu algılaması etkinleştirildiğinde, sistem, istek için kullanılabilecek proxy kümesini döndürmekten sorumlu bir ara sunucu yapılandırma betiği bulmaya çalışır. Ara sunucu yapılandırma betiği bulunursa, bir örnek kullanan bir istek için proxy bilgileri, istek akışı veya yanıt elde edildiğinde, komut dosyası indirilir, derlenir ve yerel bilgisayarda çalıştırılır <xref:System.Net.WebProxy> .  
  
 Otomatik proxy algılama, sınıfı tarafından gerçekleştirilir <xref:System.Net.WebProxy> ve istek düzeyindeki ayarları, yapılandırma dosyalarındaki ayarları ve Internet Explorer **yerel ağ (LAN)** iletişim kutusu kullanılarak belirtilen ayarları kullanabilir.  
  
> [!NOTE]
> Internet Explorer ana menüsünden **Araçlar** ' ı seçip **Internet seçenekleri**' ni seçerek Internet Explorer **yerel alan ağı (LAN) ayarları** iletişim kutusunu görüntüleyebilirsiniz. Sonra, **Bağlantılar** sekmesini seçin ve **LAN ayarları**' na tıklayın.  
  
 Otomatik ara sunucu algılaması etkinleştirildiğinde, <xref:System.Net.WebProxy> sınıfı proxy yapılandırma betiğini şu şekilde bulmaya çalışır:  
  
1. WinINet `InternetQueryOption` işlevi, Internet Explorer tarafından en son algılanan proxy yapılandırma betiğini bulmak için kullanılır.  
  
2. Betik bulunamıyorsa, <xref:System.Net.WebProxy> sınıf, betiği bulmak Için dinamik ana bilgisayar Yapılandırma Protokolü 'nü (DHCP) kullanır. DHCP sunucusu, betiğin konumuyla (ana bilgisayar adıyla) veya komut dosyasının tam URL 'siyle yanıt verebilir.  
  
3. DHCP, WPAD konağını tanımıyorsa, adı veya diğer adı olarak WPAD içeren bir konak için DNS sorgulanır.  
  
4. Konak tanımlanmamışsa ve bir ara sunucu yapılandırma betiğinin konumu Internet Explorer LAN ayarları veya bir yapılandırma dosyası tarafından belirtilmişse, bu konum kullanılır.  
  
> [!NOTE]
> NT hizmeti olarak veya ASP.NET kapsamında çalışan uygulamalar, çağıran kullanıcının Internet Explorer proxy sunucu ayarlarını (varsa) kullanır. Bu ayarlar, tüm hizmet uygulamaları için kullanılamayabilir.  
  
 Proxy 'ler, connectoıd temelinde yapılandırılır. Connectoıd, ağ bağlantısı iletişim kutusundaki bir öğedir ve bir fiziksel ağ aygıtı (bir modem veya Ethernet kartı) veya bir sanal arabirim (bir ağ aygıtı üzerinden çalışan VPN bağlantısı gibi) olabilir. Bir connectoıd değiştiğinde (örneğin, bir kablosuz bağlantı bir erişim noktasını değiştirdiğinde veya VPN etkinleştirildiğinde), proxy algılama algoritması yeniden çalıştırılır.  
  
 Varsayılan olarak, Internet Explorer ara sunucu ayarları, proxy 'yi algılamak için kullanılır. Uygulamanız etkileşimli olmayan bir hesap altında çalışıyorsa (IE proxy ayarlarını yapılandırmanın kolay bir yolu olmadan) veya IE ayarlarından farklı proxy ayarlarını kullanmak istiyorsanız, tanımlı [ \<defaultProxy> öğe (ağ ayarları)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) ve [ \<proxy> öğe (ağ ayarları)](../configure-apps/file-schema/network/proxy-element-network-settings.md) öğeleriyle bir yapılandırma dosyası oluşturarak proxy 'nizi yapılandırabilirsiniz.  
  
 Oluşturduğunuz istekler için, <xref:System.Net.WebRequest.Proxy%2A> Aşağıdaki kod örneğinde gösterildiği gibi, isteğinize sahip bir null kullanarak istek düzeyinde otomatik proxy algılamayı devre dışı bırakabilirsiniz.  
  
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
  
 Proxy olmayan istekler, uygulama etki alanının varsayılan ara sunucusunu kullanır ve bu, <xref:System.Net.WebRequest.DefaultWebProxy%2A> özelliğinde kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [\<system.Net>Öğesi (ağ ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
