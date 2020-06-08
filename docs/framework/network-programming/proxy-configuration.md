---
title: Ara Sunucu Yapılandırma
description: Uyarlamalı ve statik proxy sunucularının nasıl yapılandırılacağı hakkında bilgi edinin. Proxy yapılandırması, bir proxy sunucusunun kaynaklar için istemci isteklerini nasıl işlediğini denetler.
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
ms.openlocfilehash: d1c8b69223ab470d505d9f8007bc01b29fdc66b8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502216"
---
# <a name="proxy-configuration"></a>Ara Sunucu Yapılandırma
Proxy sunucusu, kaynaklar için istemci isteklerini işler. Bir ara sunucu, önbelleğinden istenen bir kaynağı döndürebilir veya isteği kaynağın bulunduğu sunucuya iletebilir. Proxy 'ler, uzak sunuculara gönderilen isteklerin sayısını azaltarak ağ performansını iyileştirebilir. Proxy 'ler, kaynaklara erişimi kısıtlamak için de kullanılabilir.  
  
## <a name="adaptive-proxies"></a>Uyarlamalı proxy 'Ler  
 .NET Framework, proxy 'ler iki değişken halinde gelir: Uyarlamalı ve statik. Uyarlamalı proxy 'ler, ağ yapılandırması değiştiğinde ayarlarını ayarlar. Örneğin, bir dizüstü Kullanıcı Çevirmeli ağ bağlantısı başlattığında, bir uyarlamalı ara sunucu bu değişikliği algılar, yeni yapılandırma betiğini bulur ve çalıştırır ve ayarlarını uygun şekilde ayarlar.  
  
 Uyarlamalı proxy 'ler bir yapılandırma betiği tarafından yapılandırılır (bkz. [otomatik proxy algılama](automatic-proxy-detection.md)). Betik, her protokol için bir dizi uygulama protokolü ve ara sunucu oluşturur.  
  
 Ağ ortamındaki değişiklikler sistemin yeni bir proxy kümesi kullanmasını gerektirebilir. Bir ağ bağlantısı kapalıysa veya yeni bir ağ bağlantısı başlatılmışsa, sistem yeni ortamda yapılandırma betiğinin uygun kaynağını bulmalı ve yeni betiği çalıştırmalıdır.  
  
 `usesystemdefault` [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) Yapılandırma dosyanızda öğesinin özniteliğini kullanabilirsiniz. `usesystemdefault`Özniteliği, statik ara sunucu ayarlarının (proxy adresi, atlama listesi ve yerel üzerinde atlama) Kullanıcı Için Internet Explorer proxy ayarlarından okunmayacağını denetler. Bu değer olarak ayarlanırsa `true` , Internet Explorer 'daki statik proxy ayarları kullanılacaktır. Bu değer `false` ayarlanmamışsa, yapılandırmada statik ara sunucu ayarları belirtilebilir ve Internet Explorer ara sunucu ayarlarını geçersiz kılar. Bu değer Ayrıca, `false` Uyarlamalı proxy 'lerin etkinleştirilmesi için olarak ayarlanmalıdır veya ayarlanmamış olmalıdır.  
  
 Aşağıdaki örnek, tipik bir uyarlamalı ara sunucu yapılandırmasını gösterir.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statik proxy 'Ler  
 Statik proxy 'ler genellikle bir uygulama tarafından açıkça veya bir yapılandırma dosyası bir uygulama veya sistem tarafından çağrıldığında yapılandırılır. Statik proxy 'ler, bir kurumsal ağa bağlı bir masaüstü bilgisayar gibi, topolojinin seyrek değiştiği ağlarda yararlıdır.  
  
 Statik bir proxy 'nin nasıl çalıştığını çeşitli seçenekler denetler. Aşağıdakileri belirtebilirsiniz:  
  
- Proxy adresi.  
  
- Yerel adresler için proxy 'nin atlanıp atlanmayacağı.  
  
- Bir adres kümesi için proxy 'nin atlanıp atlanmayacağı.  
  
 Aşağıdaki tabloda bir statik ara sunucu için yapılandırma seçenekleri gösterilmektedir.  
  
|Öznitelik, özellik veya yapılandırma dosyası ayarı|Description|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` veya <xref:System.Net.WebProxy.Address>|Kullanılacak proxy 'nin adresi.|  
|`bypassonlocal` veya <xref:System.Net.WebProxy.BypassProxyOnLocal>|Yerel adresler için proxy 'nin atlanıp atlanmayacağını denetler.|  
|`bypasslist` veya <xref:System.Net.WebProxy.BypassArrayList>|Normal ifadelerle, proxy 'yi atlayan bir adres kümesini açıklar.|  
|`usesystemdefault`|Statik ara sunucu ayarlarının (proxy adresi, atlama listesi ve yerel üzerinde atlama) Kullanıcı için Internet Explorer proxy ayarlarından okunmayacağını denetler. Bu değer olarak ayarlanırsa `true` , Internet Explorer 'daki statik proxy ayarları kullanılacaktır. .NET Framework 2,0 ' de, bu değer olarak ayarlandığında `true` , Internet Explorer proxy ayarları yapılandırma dosyasındaki diğer proxy ayarları tarafından geçersiz kılınmaz. .NET Framework 1,1 ' de, Internet Explorer proxy ayarları yapılandırma dosyasındaki diğer proxy ayarları tarafından geçersiz kılınabilir.<br /><br /> Bu değer `false` ayarlanmamışsa, yapılandırmada statik ara sunucu ayarları belirtilebilir ve Internet Explorer ara sunucu ayarlarını geçersiz kılar. Bu değer Ayrıca, `false` Uyarlamalı proxy 'lerin etkinleştirilmesi için olarak ayarlanmalıdır veya ayarlanmamış olmalıdır.|  
  
 Aşağıdaki örnek, tipik bir statik ara sunucu yapılandırmasını gösterir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [Otomatik Ara Sunucu Algılama](automatic-proxy-detection.md)
