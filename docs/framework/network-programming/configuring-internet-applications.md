---
title: İnternet Uygulamalarını Yapılandırma
description: .NET Framework Internet uygulamalarını yapılandırmak için <system.Net> öğesinin nasıl kullanılacağını öğrenin. Bu makale örnek kod içerir.
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
ms.openlocfilehash: 760a4ac7cec9abeabfc372c3be5bd3860a6fb03a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502645"
---
# <a name="configuring-internet-applications"></a>İnternet Uygulamalarını Yapılandırma
[ \<system.Net> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md) yapılandırma öğesi, uygulamalar için ağ yapılandırma bilgilerini içerir. [ \<system.Net> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md) öğesini kullanarak, proxy sunucuları ayarlayabilir, bağlantı yönetim parametrelerini ayarlayabilir ve özel kimlik doğrulaması ve istek modüllerini uygulamanıza ekleyebilirsiniz.  
  
 [ \<defaultProxy> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) öğesi, sınıfı tarafından döndürülen proxy sunucusunu tanımlar `GlobalProxySelection` . <xref:System.Net.HttpWebRequest>Kendi <xref:System.Net.HttpWebRequest.Proxy%2A> özelliği belirli bir değere ayarlanmış olmayan her türlü, varsayılan proxy 'yi kullanır. Proxy adresini ayarlamaya ek olarak, proxy 'yi kullanmayacak sunucu adreslerinin bir listesini oluşturabilir ve proxy 'nin yerel adresler için kullanılması gerekmediğini belirtebilirsiniz.  
  
 Microsoft Internet Explorer ayarlarının, son önceliğe sahip yapılandırma ayarları ile birleştirildiğine dikkat edin.  
  
 Aşağıdaki örnek, varsayılan proxy sunucu adresini olarak ayarlar `http://proxyserver` , proxy 'nin yerel adresler için kullanılmayacağını belirtir ve contoso.com etki alanında bulunan sunuculara yapılan tüm isteklerin proxy 'yi atmasını belirtir.  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 Belirli bir sunucuya veya diğer tüm sunuculara yapılabilecek kalıcı bağlantıların sayısını yapılandırmak için [ \<connectionManagement> öğe (ağ ayarları)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) öğesini kullanın. Aşağıdaki örnek, uygulamayı sunucusuna iki kalıcı bağlantı `www.contoso.com` , 192.168.1.2 IP adresi ile sunucuya dört kalıcı bağlantı ve diğer tüm sunuculara kalıcı bir bağlantı kullanacak şekilde yapılandırır.  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 Özel kimlik doğrulama modülleri, [ \<authenticationModules> öğe (ağ ayarları)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) öğesi ile yapılandırılır. Özel kimlik doğrulama modülleri arabirimini gerçekleştirmelidir <xref:System.Net.IAuthenticationModule> .  
  
 Aşağıdaki örnek bir özel kimlik doğrulama modülünü yapılandırır.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Uygulamanızı Internet kaynaklarından bilgi istemek için özel protokole özgü modüller kullanacak şekilde yapılandırmak için [ \<webRequestModules> öğesi (ağ ayarları)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) öğesini kullanabilirsiniz. Belirtilen modüller <xref:System.Net.IWebRequestCreate> arabirimini uygulamalıdır. Aşağıdaki örnekte olduğu gibi yapılandırma dosyasında özel modülünüzü belirterek varsayılan HTTP, HTTPS ve dosya isteği modüllerini geçersiz kılabilirsiniz.  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'te Ağ Programlaması](index.md)
- [Ağ Ayarları Şeması](../configure-apps/file-schema/network/index.md)
- [\<system.Net>Öğesi (ağ ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
