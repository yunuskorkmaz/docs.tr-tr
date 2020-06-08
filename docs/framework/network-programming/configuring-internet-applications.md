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
# <a name="configuring-internet-applications"></a><span data-ttu-id="a46d5-104">İnternet Uygulamalarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a46d5-104">Configuring Internet Applications</span></span>
<span data-ttu-id="a46d5-105">[ \<system.Net> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md) yapılandırma öğesi, uygulamalar için ağ yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a46d5-105">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="a46d5-106">[ \<system.Net> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md) öğesini kullanarak, proxy sunucuları ayarlayabilir, bağlantı yönetim parametrelerini ayarlayabilir ve özel kimlik doğrulaması ve istek modüllerini uygulamanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a46d5-106">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="a46d5-107">[ \<defaultProxy> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) öğesi, sınıfı tarafından döndürülen proxy sunucusunu tanımlar `GlobalProxySelection` .</span><span class="sxs-lookup"><span data-stu-id="a46d5-107">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="a46d5-108"><xref:System.Net.HttpWebRequest>Kendi <xref:System.Net.HttpWebRequest.Proxy%2A> özelliği belirli bir değere ayarlanmış olmayan her türlü, varsayılan proxy 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a46d5-108">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="a46d5-109">Proxy adresini ayarlamaya ek olarak, proxy 'yi kullanmayacak sunucu adreslerinin bir listesini oluşturabilir ve proxy 'nin yerel adresler için kullanılması gerekmediğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a46d5-109">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="a46d5-110">Microsoft Internet Explorer ayarlarının, son önceliğe sahip yapılandırma ayarları ile birleştirildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a46d5-110">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="a46d5-111">Aşağıdaki örnek, varsayılan proxy sunucu adresini olarak ayarlar `http://proxyserver` , proxy 'nin yerel adresler için kullanılmayacağını belirtir ve contoso.com etki alanında bulunan sunuculara yapılan tüm isteklerin proxy 'yi atmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a46d5-111">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="a46d5-112">Belirli bir sunucuya veya diğer tüm sunuculara yapılabilecek kalıcı bağlantıların sayısını yapılandırmak için [ \<connectionManagement> öğe (ağ ayarları)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a46d5-112">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="a46d5-113">Aşağıdaki örnek, uygulamayı sunucusuna iki kalıcı bağlantı `www.contoso.com` , 192.168.1.2 IP adresi ile sunucuya dört kalıcı bağlantı ve diğer tüm sunuculara kalıcı bir bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a46d5-113">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="a46d5-114">Özel kimlik doğrulama modülleri, [ \<authenticationModules> öğe (ağ ayarları)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) öğesi ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="a46d5-114">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="a46d5-115">Özel kimlik doğrulama modülleri arabirimini gerçekleştirmelidir <xref:System.Net.IAuthenticationModule> .</span><span class="sxs-lookup"><span data-stu-id="a46d5-115">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="a46d5-116">Aşağıdaki örnek bir özel kimlik doğrulama modülünü yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a46d5-116">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="a46d5-117">Uygulamanızı Internet kaynaklarından bilgi istemek için özel protokole özgü modüller kullanacak şekilde yapılandırmak için [ \<webRequestModules> öğesi (ağ ayarları)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a46d5-117">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="a46d5-118">Belirtilen modüller <xref:System.Net.IWebRequestCreate> arabirimini uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a46d5-118">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="a46d5-119">Aşağıdaki örnekte olduğu gibi yapılandırma dosyasında özel modülünüzü belirterek varsayılan HTTP, HTTPS ve dosya isteği modüllerini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a46d5-119">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a46d5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a46d5-120">See also</span></span>

- [<span data-ttu-id="a46d5-121">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="a46d5-121">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="a46d5-122">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a46d5-122">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="a46d5-123">\<system.Net>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="a46d5-123">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
