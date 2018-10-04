---
title: Internet uygulamalarını yapılandırma
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d2f3f015689510237142572f230b53ba7bd393ca
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780959"
---
# <a name="configuring-internet-applications"></a>Internet uygulamalarını yapılandırma
[ \<System.Net > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) yapılandırma öğesi, uygulamalar için ağ yapılandırma bilgileri içerir. Kullanarak [ \<system.Net > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) öğesini ayarlayın proxy sunucuları, bağlantı yönetimi parametrelerinin ve uygulamanıza özel kimlik doğrulama ve istek modülleri dahil.  
  
 [ \<DefaultProxy > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) öğesi tarafından döndürülen proxy sunucusu tanımlar `GlobalProxySelection` sınıfı. Tüm <xref:System.Net.HttpWebRequest> olmayan kendi <xref:System.Net.HttpWebRequest.Proxy%2A> özelliği belirli bir değere ayarlanmış varsayılan proxy kullanır. Proxy adresi ayarı yanı sıra proxy kullanmaz sunucu adresleri listesi oluşturabilirsiniz ve proxy yerel adresler için kullanılmamalıdır belirtebilirsiniz.  
  
 Microsoft Internet Explorer ayarları, ikinci alma önceliğe sahip yapılandırma ayarlarıyla birleştirildiğini dikkat edin önemlidir.  
  
 Aşağıdaki örnekte varsayılan proxy sunucusu adresi ayarlar http://proxyserver, proxy yerel adresler için kullanılmamalıdır ve contoso.com etki alanında bulunan sunucular için tüm istekleri proxy atlama belirtir.  
  
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
  
 Kullanım [ \<connectionManagement > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) belirli bir sunucuya veya diğer tüm sunucular için yapılan kalıcı bağlantı sayısını yapılandırmak için öğesi. Aşağıdaki örnek iki kalıcı bağlantı sunucusu www.contoso.com, sunucunun IP adresiyle 192.168.1.2 dört kalıcı bağlantılar ve diğer tüm sunucuları tek bir kalıcı bağlantı kullanmak üzere uygulamayı yapılandırır.  
  
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
  
 Özel kimlik doğrulama modülleri ile yapılandırılmış [ \<authenticationModules > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) öğesi. Özel kimlik doğrulama modülleri uygulanmalı <xref:System.Net.IAuthenticationModule> arabirimi.  
  
 Aşağıdaki örnek bir özel kimlik doğrulama modülü yapılandırır.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Kullanabileceğiniz [ \<webRequestModules > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) özel protokole özgü modüller, Internet kaynaklarını isteği bilgilerini kullanmak için uygulamanızı yapılandırma öğesi. Belirtilen modülleri uygulamalıdır <xref:System.Net.IWebRequestCreate> arabirimi. Yapılandırma dosyasında aşağıdaki örnekte olduğu gibi özel modül belirterek varsayılan HTTP, HTTPS ve dosya isteği modülleri geçersiz kılabilirsiniz.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework'te Ağ Programlaması](../../../docs/framework/network-programming/index.md)  
 [Ağ Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<system.Net > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
