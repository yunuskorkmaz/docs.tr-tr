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
# <a name="configuring-internet-applications"></a><span data-ttu-id="5d656-102">İnternet Uygulamalarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5d656-102">Configuring Internet Applications</span></span>
<span data-ttu-id="5d656-103">[ \<system.Net> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md) yapılandırma öğesi, uygulamalar için ağ yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5d656-103">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="5d656-104">system.Net [ \<> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/system-net-element-network-settings.md) öğesini kullanarak proxy sunucuları ayarlayabilir, bağlantı yönetimi parametrelerini ayarlayabilir ve uygulamanızda özel kimlik doğrulama ve istek modülleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d656-104">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="5d656-105">[Varsayılan Proxy> Öğesi (Ağ Ayarları) öğesi, sınıf tarafından döndürülen proxy sunucusunu tanımlar. \<](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) `GlobalProxySelection`</span><span class="sxs-lookup"><span data-stu-id="5d656-105">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="5d656-106">Belirli <xref:System.Net.HttpWebRequest> bir değeriçin <xref:System.Net.HttpWebRequest.Proxy%2A> ayarlanmış kendi özelliği olmayan herhangi bir varsayılan proxy kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d656-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="5d656-107">Proxy adresini ayarlamaya ek olarak, proxy'yi kullanmayan sunucu adreslerinin bir listesini oluşturabilir ve proxy'nin yerel adresler için kullanılmaması gerektiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d656-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="5d656-108">Microsoft Internet Explorer ayarlarının yapılandırma ayarlarıyla birleştirildiğinden, ikincisinin öncelikli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5d656-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="5d656-109">Aşağıdaki örnekte varsayılan proxy sunucu `http://proxyserver`adresi , proxy yerel adresler için kullanılmaması gerektiğini gösterir ve contoso.com etki alanında bulunan sunuculara tüm istekleri proxy atlamak gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d656-109">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
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
  
 <span data-ttu-id="5d656-110">Belirli bir sunucuya veya diğer tüm sunuculara yapIlebilen kalıcı bağlantı sayısını yapılandırmak için [ \<bağlantı Yönetimi> Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d656-110">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="5d656-111">Aşağıdaki örnek, uygulamayı sunucuya `www.contoso.com`iki kalıcı bağlantı, IP adresi 192.168.1.2 olan sunucuya dört kalıcı bağlantı ve diğer tüm sunuculara kalıcı bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5d656-111">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
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
  
 <span data-ttu-id="5d656-112">Özel kimlik doğrulama modülleri, [ \<Element (Ağ Ayarları)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) öğesi> ile kimlik doğrulama modülleri ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5d656-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="5d656-113">Özel kimlik doğrulama modülleri <xref:System.Net.IAuthenticationModule> arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d656-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="5d656-114">Aşağıdaki örnek, özel bir kimlik doğrulama modüllerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5d656-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="5d656-115">Uygulamanızı Internet kaynaklarından bilgi istemek için protokole özel özel modüller kullanacak şekilde yapılandırmak için [ \<webRequestModules> Element (Ağ Ayarları)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d656-115">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="5d656-116">Belirtilen modüller <xref:System.Net.IWebRequestCreate> arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d656-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="5d656-117">Aşağıdaki örnekte olduğu gibi yapılandırma dosyasında özel modülünüzü belirterek varsayılan HTTP, HTTPS ve dosya istek modüllerini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d656-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d656-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d656-118">See also</span></span>

- [<span data-ttu-id="5d656-119">.NET Framework'te Ağ Programlaması</span><span class="sxs-lookup"><span data-stu-id="5d656-119">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="5d656-120">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5d656-120">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="5d656-121">\<system.Net> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="5d656-121">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
