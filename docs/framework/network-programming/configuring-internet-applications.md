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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078428"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="fe4b2-102">Internet uygulamalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fe4b2-102">Configuring Internet Applications</span></span>
<span data-ttu-id="fe4b2-103">[ \<System.Net > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) yapılandırma öğesi, uygulamalar için ağ yapılandırma bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-103">The [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="fe4b2-104">Kullanarak [ \<system.Net > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) öğesini ayarlayın proxy sunucuları, bağlantı yönetimi parametrelerinin ve uygulamanıza özel kimlik doğrulama ve istek modülleri dahil.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-104">Using the [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="fe4b2-105">[ \<DefaultProxy > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) öğesi tarafından döndürülen proxy sunucusu tanımlar `GlobalProxySelection` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-105">The [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="fe4b2-106">Tüm <xref:System.Net.HttpWebRequest> olmayan kendi <xref:System.Net.HttpWebRequest.Proxy%2A> özelliği belirli bir değere ayarlanmış varsayılan proxy kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="fe4b2-107">Proxy adresi ayarı yanı sıra proxy kullanmaz sunucu adresleri listesi oluşturabilirsiniz ve proxy yerel adresler için kullanılmamalıdır belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="fe4b2-108">Microsoft Internet Explorer ayarları, ikinci alma önceliğe sahip yapılandırma ayarlarıyla birleştirildiğini dikkat edin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="fe4b2-109">Aşağıdaki örnekte varsayılan proxy sunucusu adresi ayarlar http://proxyserver, proxy yerel adresler için kullanılmamalıdır ve contoso.com etki alanında bulunan sunucular için tüm istekleri proxy atlama belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-109">The following example sets the default proxy server address to http://proxyserver, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="fe4b2-110">Kullanım [ \<connectionManagement > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) belirli bir sunucuya veya diğer tüm sunucular için yapılan kalıcı bağlantı sayısını yapılandırmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-110">Use the [\<connectionManagement> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="fe4b2-111">Aşağıdaki örnek iki kalıcı bağlantı sunucusu www.contoso.com, sunucunun IP adresiyle 192.168.1.2 dört kalıcı bağlantılar ve diğer tüm sunucuları tek bir kalıcı bağlantı kullanmak üzere uygulamayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-111">The following example configures the application to use two persistent connections to the server www.contoso.com, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="fe4b2-112">Özel kimlik doğrulama modülleri ile yapılandırılmış [ \<authenticationModules > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="fe4b2-113">Özel kimlik doğrulama modülleri uygulanmalı <xref:System.Net.IAuthenticationModule> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="fe4b2-114">Aşağıdaki örnek bir özel kimlik doğrulama modülü yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="fe4b2-115">Kullanabileceğiniz [ \<webRequestModules > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) özel protokole özgü modüller, Internet kaynaklarını isteği bilgilerini kullanmak için uygulamanızı yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-115">You can use the [\<webRequestModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="fe4b2-116">Belirtilen modülleri uygulamalıdır <xref:System.Net.IWebRequestCreate> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="fe4b2-117">Yapılandırma dosyasında aşağıdaki örnekte olduğu gibi özel modül belirterek varsayılan HTTP, HTTPS ve dosya isteği modülleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe4b2-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe4b2-118">See Also</span></span>  
 [<span data-ttu-id="fe4b2-119">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="fe4b2-119">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="fe4b2-120">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fe4b2-120">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="fe4b2-121">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="fe4b2-121">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
