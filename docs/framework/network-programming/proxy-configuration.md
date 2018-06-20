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
manager: markl
ms.openlocfilehash: 6cf25d3d7dcde963f06729794716b75dffdb64ae
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207371"
---
# <a name="proxy-configuration"></a>Proxy yapılandırması
Bir proxy sunucu kaynakları için istemci isteklerini işler. Bir proxy, istenen kaynak, önbellekten döndürür veya kaynağının bulunduğu sunucu isteği iletin. Proxy'leri uzak sunuculara gönderilen isteklerin sayısını azaltarak ağ performansını iyileştirebilir. Proxy'leri kaynaklara erişimi kısıtlamak için de kullanılabilir.  
  
## <a name="adaptive-proxies"></a>Uyarlamalı proxy'leri  
 .NET Framework'teki proxy'leri iki çeşit olarak bulunur: Uyarlamalı ve statik. Ağ yapılandırma değiştiğinde Uyarlamalı proxy'leri ayarlarına ayarlayın. Örneğin, bir dizüstü bilgisayar kullanıcı bir çevirmeli ağ bağlantısı başlarsa, Uyarlamalı proxy bu değişikliği algılar, bulmak ve kendi yeni yapılandırma komut dosyasını çalıştırın ve kendi ayarlarını uygun şekilde.  
  
 Uyarlamalı proxy'leri yapılandırma komut dosyası tarafından yapılandırılır (bkz [Otomatik Proxy algılama](../../../docs/framework/network-programming/automatic-proxy-detection.md)). Komut dosyasını bir dizi uygulama protokolleri ve her protokol için bir proxy oluşturur.  
  
 Ağ ortamında değişiklikleri sistem proxy'leri yeni bir dizi kullanmanızı gerektirebilir. Bir ağ bağlantısı arıza ya da yeni bir ağ bağlantısı başlatıldı, sistem yeni ortamındaki yapılandırma komut dosyası, uygun kaynak bulmak ve yeni komut dosyasını çalıştırın.  
  
 Kullanabileceğiniz `usesystemdefault` özniteliği [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) yapılandırma dosyanızda öğesi. `usesystemdefault` Statik proxy ayarları (proxy adresi, atlama listesi ve yerel atlama) kullanıcı için Internet Explorer proxy ayarları okumalısınız olup olmadığını kontrol eder özniteliği. Bu değer ayarlanırsa `true`, Internet Explorer'dan statik proxy ayarları kullanılır. Bu değer ise `false` veya ayarlanmadı, statik proxy ayarlarını yapılandırma dosyasında belirtilen ve Internet Explorer proxy ayarları geçersiz kılar. Bu değer ayrıca ayarlanmalıdır `false` veya uyarlamalı proxy'leri etkinleştirilmesi ayarlı değil.  
  
 Aşağıdaki örnek tipik Uyarlamalı proxy yapılandırmasını gösterir.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statik proxy'leri  
 Statik proxy'leri genellikle açıkça bir uygulama tarafından veya bir yapılandırma dosyası bir uygulama veya sistem tarafından çağrıldığında yapılandırılır. Statik proxy'leri içinde topoloji, bir kurumsal ağa bağlı bir masaüstü bilgisayar gibi sık değişmeyen ağlarda faydalıdır.  
  
 Çeşitli seçenekler statik proxy nasıl çalıştığını denetler. Şunları belirtebilirsiniz:  
  
-   Proxy adresi.  
  
-   Proxy yerel adresler için atlanmasına.  
  
-   Proxy adresleri kümesini için atlanmasına.  
  
 Aşağıdaki tabloda statik bir proxy sunucu için yapılandırma seçeneklerini gösterir.  
  
|Öznitelik, özellik veya yapılandırma dosyası ayarı|Açıklama|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` Veya <xref:System.Net.WebProxy.Address>|Kullanılacak proxy adresi.|  
|`bypassonlocal` Veya <xref:System.Net.WebProxy.BypassProxyOnLocal>|Yerel adresler için proxy atlanır olup olmadığını denetler.|  
|`bypasslist` Veya <xref:System.Net.WebProxy.BypassArrayList>|, Normal ifadelerle bir proxy atlama adresi açıklar.|  
|`usesystemdefault`|(Proxy adresi atlama listesine ve yerel atlama) statik proxy ayarlarını gerekip gerekmediğini kullanıcı için Internet Explorer proxy ayarlarını okunmasına denetler. Bu değer ayarlanırsa `true`, Internet Explorer'dan statik proxy ayarları kullanılır. Bu değer ayarlandığında .NET Framework 2.0 `true`, Internet Explorer proxy ayarlarını yapılandırma dosyasındaki diğer proxy ayarları tarafından geçersiz kılınmaz. .NET Framework 1.1, Internet Explorer proxy ayarlarını diğer proxy ayarlarını yapılandırma dosyasında geçersiz kılınabilir.<br /><br /> Bu değer ise `false` veya ayarlanmadı, statik proxy ayarlarını yapılandırma dosyasında belirtilen sonra Internet Explorer proxy ayarları geçersiz kılar. Bu değer ayrıca ayarlanmalıdır `false` veya uyarlamalı proxy'leri etkinleştirilmesi ayarlı değil.|  
  
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
