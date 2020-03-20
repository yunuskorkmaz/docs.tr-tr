---
title: İnternet Uygulamalarını Yapılandırma
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
ms.openlocfilehash: ee4dc87383153ae4e8df0a3bed7cce5220e65405
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048625"
---
# <a name="configuring-internet-applications"></a>İnternet Uygulamalarını Yapılandırma
[ \<system.Net> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md) yapılandırma öğesi, uygulamalar için ağ yapılandırma bilgilerini içerir. system.Net [ \<> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md) öğesini kullanarak proxy sunucuları ayarlayabilir, bağlantı yönetimi parametrelerini ayarlayabilir ve uygulamanızda özel kimlik doğrulama ve istek modülleri ekleyebilirsiniz.  
  
 [Varsayılan Proxy> Öğesi (Ağ Ayarları) öğesi, sınıf tarafından döndürülen proxy sunucusunu tanımlar. \<](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) `GlobalProxySelection` Belirli <xref:System.Net.HttpWebRequest> bir değeriçin <xref:System.Net.HttpWebRequest.Proxy%2A> ayarlanmış kendi özelliği olmayan herhangi bir varsayılan proxy kullanır. Proxy adresini ayarlamaya ek olarak, proxy'yi kullanmayan sunucu adreslerinin bir listesini oluşturabilir ve proxy'nin yerel adresler için kullanılmaması gerektiğini belirtebilirsiniz.  
  
 Microsoft Internet Explorer ayarlarının yapılandırma ayarlarıyla birleştirildiğinden, ikincisinin öncelikli olduğunu unutmayın.  
  
 Aşağıdaki örnekte varsayılan proxy sunucu `http://proxyserver`adresi , proxy yerel adresler için kullanılmaması gerektiğini gösterir ve contoso.com etki alanında bulunan sunuculara tüm istekleri proxy atlamak gerektiğini belirtir.  
  
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
  
 Belirli bir sunucuya veya diğer tüm sunuculara yapIlebilen kalıcı bağlantı sayısını yapılandırmak için [ \<bağlantı Yönetimi> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) öğesini kullanın. Aşağıdaki örnek, uygulamayı sunucuya `www.contoso.com`iki kalıcı bağlantı, IP adresi 192.168.1.2 olan sunucuya dört kalıcı bağlantı ve diğer tüm sunuculara kalıcı bağlantı kullanacak şekilde yapılandırır.  
  
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
  
 Özel kimlik doğrulama modülleri, [ \<Element (Ağ Ayarları)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) öğesi> ile kimlik doğrulama modülleri ile yapılandırılır. Özel kimlik doğrulama modülleri <xref:System.Net.IAuthenticationModule> arabirimi uygulamalıdır.  
  
 Aşağıdaki örnek, özel bir kimlik doğrulama modüllerini yapılandırır.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Uygulamanızı Internet kaynaklarından bilgi istemek için protokole özel özel modüller kullanacak şekilde yapılandırmak için [ \<webRequestModules> Element (Ağ Ayarları)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) öğesini kullanabilirsiniz. Belirtilen modüller <xref:System.Net.IWebRequestCreate> arabirimi uygulamalıdır. Aşağıdaki örnekte olduğu gibi yapılandırma dosyasında özel modülünüzü belirterek varsayılan HTTP, HTTPS ve dosya istek modüllerini geçersiz kılabilirsiniz.  
  
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
- [\<system.Net> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
