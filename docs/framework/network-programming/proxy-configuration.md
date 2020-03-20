---
title: Ara Sunucu Yapılandırma
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
ms.openlocfilehash: 1fbfe25b90e810ff96924a2341582ff3f5ee5e5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047351"
---
# <a name="proxy-configuration"></a>Ara Sunucu Yapılandırma
Proxy sunucusu, istemci kaynakları isteklerini işler. Proxy, istenen kaynağı önbelleğinden döndürebilir veya isteği kaynağın bulunduğu sunucuya iletebilir. Ekseksiler, uzak sunuculara gönderilen istek sayısını azaltarak ağ performansını artırabilir. Ekseksitler, kaynaklara erişimi kısıtlamak için de kullanılabilir.  
  
## <a name="adaptive-proxies"></a>Adaptif Proxies  
 .NET Framework'de yakınlıklar iki çeşitten gelir: uyarlanabilir ve statik. Uyarlanabilir yakınlıklar, ağ yapılandırması değiştiğinde ayarlarını ayarlar. Örneğin, bir dizüstü bilgisayar kullanıcısı çevirmeli ağ bağlantısı başlatırsa, uyarlanabilir bir proxy bu değişikliği tanır, yeni yapılandırma komut dosyasını keşfeder ve çalıştırAbilir ve ayarlarını uygun şekilde ayarlar.  
  
 Uyarlanabilir proxy'ler bir yapılandırma komut dosyası tarafından yapılandırılır (bkz. [Otomatik Proxy Algılama).](automatic-proxy-detection.md) Komut dosyası, her protokol için bir uygulama protokolü kümesi ve proxy oluşturur.  
  
 Ağ ortamındaki değişiklikler, sistemin yeni bir yakınlık kümesi kullanmasını gerektirebilir. Bir ağ bağlantısı kapatılırsa veya yeni bir ağ bağlantısı başlatılması durumunda, sistemin yapılandırma komut dosyasının uygun kaynağını yeni ortamda bulması ve yeni komut dosyasını çalıştırması gerekir.  
  
 Yapılandırma dosyanızdaki `usesystemdefault` öğenin [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) özniteliğini kullanabilirsiniz. Öznitelik, `usesystemdefault` statik proxy ayarlarının (proxy adresi, bypass listesi ve yerel deki bypass) kullanıcı için Internet Explorer proxy ayarlarından okunup okunmayacağını denetler. Bu değer `true`ayarlanmışsa, Internet Explorer'ın statik proxy ayarları kullanılır. Bu değer `false` ayarlanmış sa veya ayarlanmamışsa, statik proxy ayarları yapılandırmada belirtilebilir ve Internet Explorer proxy ayarlarını geçersiz kılar. Uyarlanabilir yakınlıkların etkinleştirilmesi için bu değerin ayarlanmaması `false` veya ayarlanmaması gerekir.  
  
 Aşağıdaki örnek, tipik bir uyarlanabilir proxy yapılandırmasını gösterir.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statik Proxies  
 Statik ekseksenler genellikle bir uygulama tarafından veya bir yapılandırma dosyası bir uygulama veya sistem tarafından çağrıldığında açıkça yapılandırılır. Statik yakınlıklar, topolojinin şirket ağına bağlı bir masaüstü bilgisayar gibi seyrek değiştiği ağlarda yararlıdır.  
  
 Statik proxy'nin nasıl çalıştığını çeşitli seçenekler denetler. Aşağıdakileri belirtebilirsiniz:  
  
- Vekilin adresi.  
  
- Proxy yerel adresler için atlalı olup olmadığını.  
  
- Proxy adresleri kümesi için atlalı olup olmadığını.  
  
 Aşağıdaki tablostatik bir proxy için yapılandırma seçeneklerini gösterir.  
  
|Öznitelik, özellik veya yapılandırma dosya ayarı|Açıklama|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` veya <xref:System.Net.WebProxy.Address>|Kullanılacak proxy adresi.|  
|`bypassonlocal` veya <xref:System.Net.WebProxy.BypassProxyOnLocal>|Proxy'nin yerel adresler için atlanıp atlanıp atlanıp atlılmayacağını denetler.|  
|`bypasslist` veya <xref:System.Net.WebProxy.BypassArrayList>|Düzenli ifadelerle proxy'yi atlayan bir adres kümesini açıklar.|  
|`usesystemdefault`|Statik proxy ayarlarının (proxy adresi, bypass listesi ve yerel deki bypass) kullanıcı için Internet Explorer proxy ayarlarından okunup okunmayacağını denetler. Bu değer `true`,internet explorer statik proxy ayarları olarak ayarlanırsa kullanılır. .NET Framework 2.0'da bu `true`değer ayarlandığında, Internet Explorer proxy ayarları yapılandırma dosyasındaki diğer proxy ayarları tarafından geçersiz kılınmaz. .NET Framework 1.1'de, Internet Explorer proxy ayarları yapılandırma dosyasındaki diğer proxy ayarları tarafından geçersiz kılınabilir.<br /><br /> Bu değer `false` ayarlanmış sa veya ayarlanmamışsa, statik proxy ayarları yapılandırmada belirtilebilir ve Internet Explorer proxy ayarlarını geçersiz kılar. Uyarlanabilir yakınlıkların etkinleştirilmesi için bu değerin ayarlanmaması `false` veya ayarlanmaması gerekir.|  
  
 Aşağıdaki örnek, tipik bir statik proxy yapılandırmasını gösterir.  
  
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
