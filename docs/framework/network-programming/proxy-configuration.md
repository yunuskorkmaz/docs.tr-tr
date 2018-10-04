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
ms.openlocfilehash: f4ae905b7500a8555691557b264985acf538d075
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48776824"
---
# <a name="proxy-configuration"></a>Proxy yapılandırması
Bir proxy sunucu kaynakları için istemci isteklerini işler. Bir proxy önbelleğinden istenen kaynak döndürebilen veya kaynağının bulunduğu sunucu isteği iletir. Proxy, uzak sunucuya gönderilen istek sayısını azaltarak ağ performansını iyileştirebilir. Proxy'leri, kaynaklara erişimi kısıtlamak için de kullanılabilir.  
  
## <a name="adaptive-proxies"></a>Uyarlamalı proxy'ler  
 .NET Framework'teki proxy'leri iki çeşit olarak bulunur: Uyarlamalı ve statik. Ağ yapılandırması değiştiğinde Uyarlamalı proxy ayarlarını değiştirebilir. Örneğin, bir dizüstü kullanıcı bir çevirmeli ağ bağlantısı başlarsa, Uyarlamalı bir proxy bu değişikliği tanıması, bulmak, yeni bir yapılandırma betiği çalıştırın ve kendi ayarlarını uygun şekilde.  
  
 Uyarlamalı proxy'leri, bir yapılandırma betiği tarafından yapılandırılır (bkz [Otomatik Proxy algılama](../../../docs/framework/network-programming/automatic-proxy-detection.md)). Betik, bir dizi uygulama protokolleri ve her protokol için bir proxy oluşturur.  
  
 Ağ ortamınızda değişiklikler Sistem proxy yeni bir dizi gerektirebilir. Bir ağ bağlantısı arıza ya da yeni bir ağ bağlantısı başlatılır, sistem uygun kaynak yeni ortama yapılandırma betiğinin keşfedin ve yeni betiği çalıştırın.  
  
 Kullanabileceğiniz `usesystemdefault` özniteliği [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) yapılandırma dosyanızdaki öğesi. `usesystemdefault` Kullanıcı için Internet Explorer proxy ayarlarını (proxy adresi, atlama listesi ve yerel atlama) statik proxy ayarlarını okunur olmadığını denetimleri özniteliği. Bu değer ayarlanırsa `true`, Internet Explorer'dan statik proxy ayarları kullanılacaktır. Bu değer ise `false` veya ayarlanmadı, statik proxy ayarlarını yapılandırmada belirtilen ve Internet Explorer proxy ayarlarını geçersiz kılar. Bu değer ayrıca ayarlanmalıdır `false` veya uyarlamalı proxy'leri etkinleştirilmesi için ayarlanmadı.  
  
 Aşağıdaki örnek, tipik Uyarlamalı proxy yapılandırmasını gösterir.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statik proxy'ler  
 Statik proxy'leri genellikle açıkça bir uygulama tarafından veya bir yapılandırma dosyası bir uygulama veya sistem tarafından çağrıldığında yapılandırılır. Statik proxy'leri, topoloji, bir şirket ağına bağlı bir masaüstü bilgisayar gibi sık değişmeyen ağlardaki yararlıdır.  
  
 Çeşitli seçenekler, statik bir proxy nasıl çalıştığını denetler. Aşağıdakileri belirtebilirsiniz:  
  
-   Proxy adresi.  
  
-   Proxy yerel adresler için atlanmasına.  
  
-   Proxy için adresleri kümesini atlanmasına.  
  
 Aşağıdaki tabloda, statik bir ara sunucu yapılandırma seçenekleri gösterilmektedir.  
  
|Öznitelik, özellik veya yapılandırma dosyası ayarı|Açıklama|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` veya <xref:System.Net.WebProxy.Address>|Kullanılacak proxy adresi.|  
|`bypassonlocal` veya <xref:System.Net.WebProxy.BypassProxyOnLocal>|Yerel adresler için proxy atlanır olup olmadığını denetler.|  
|`bypasslist` veya <xref:System.Net.WebProxy.BypassArrayList>|, Normal ifadeler ile bir proxy atlama adresleri kümesini açıklar.|  
|`usesystemdefault`|Kullanıcı için Internet Explorer proxy ayarlarını (proxy adresi atlama listesine ve yerel atlama) statik proxy ayarlarını gerekip gerekmediğini okunması denetler. Bu değer ayarlanırsa `true`, Internet Explorer statik proxy ayarları kullanılacaktır. Bu değer ayarlandığında .NET Framework 2.0 `true`, Internet Explorer proxy ayarlarını yapılandırma dosyasındaki diğer proxy ayarları geçersiz kılınmaz. .NET Framework 1.1, Internet Explorer proxy ayarlarının diğer proxy ayarlarını yapılandırma dosyasındaki kılınabilir.<br /><br /> Bu değer ise `false` veya ayarlanmadı, ardından statik proxy ayarlarını yapılandırmada belirtilen ve Internet Explorer proxy ayarlarını geçersiz kılar. Bu değer ayrıca ayarlanmalıdır `false` veya uyarlamalı proxy'leri etkinleştirilmesi için ayarlanmadı.|  
  
 Aşağıdaki örnek bir genel statik proxy yapılandırmasını gösterir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [Otomatik Ara Sunucu Algılama](../../../docs/framework/network-programming/automatic-proxy-detection.md)
