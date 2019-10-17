---
title: YükDengeleme
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: 572537826074dd51b56f1cae9edb767708bc1c3d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321026"
---
# <a name="load-balancing"></a><span data-ttu-id="493d6-102">YükDengeleme</span><span class="sxs-lookup"><span data-stu-id="493d6-102">Load Balancing</span></span>
<span data-ttu-id="493d6-103">Windows Communication Foundation (WCF) uygulamalarının kapasitesini artırmanın bir yolu, bunları yük dengeli bir sunucu grubuna dağıtarak bunları ölçeklendirmektir.</span><span class="sxs-lookup"><span data-stu-id="493d6-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="493d6-104">WCF uygulamaları, Windows Ağ Yükü Dengeleme gibi yazılım yük dengeleyiciler ve donanım tabanlı yük dengeleme gereçlerinin yanı sıra standart Yük Dengeleme teknikleri kullanılarak yük dengelenebilir.</span><span class="sxs-lookup"><span data-stu-id="493d6-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="493d6-105">Aşağıdaki bölümlerde, sistem tarafından sunulan çeşitli bağlamalar kullanılarak oluşturulan yük dengeleme WCF uygulamalarına ilişkin konular ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="493d6-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="493d6-106">Temel HTTP bağlamasıyla Yük Dengeleme</span><span class="sxs-lookup"><span data-stu-id="493d6-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="493d6-107">Yük Dengeleme açısından, <xref:System.ServiceModel.BasicHttpBinding> kullanılarak iletişim kuran WCF uygulamaları diğer yaygın HTTP ağ trafiği türlerinden (statik HTML içeriği, ASP.NET sayfaları veya ASMX Web Hizmetleri) farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="493d6-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="493d6-108">Bu bağlamayı kullanan WCF kanalları doğal olarak durum bilgisdir ve kanal kapandığında bağlantılarını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="493d6-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="493d6-109">Bu nedenle, <xref:System.ServiceModel.BasicHttpBinding> var olan HTTP Yük Dengeleme teknikleri ile iyi şekilde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="493d6-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="493d6-110">Varsayılan olarak <xref:System.ServiceModel.BasicHttpBinding>, istemcilerin bunları destekleyen hizmetlere kalıcı bağlantılar kurmasını sağlayan `Keep-Alive` değerli iletilerde bir bağlantı HTTP üst bilgisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="493d6-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="493d6-111">Bu yapılandırma, daha önce oluşturulmuş bağlantılar daha sonraki iletileri aynı sunucuya göndermek için yeniden kullanılabilir olduğundan, gelişmiş aktarım hızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="493d6-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="493d6-112">Bununla birlikte, bağlantı yeniden kullanımı, istemcilerin yük dengeli gruptaki belirli bir sunucuyla kesin bir şekilde ilişkili hale gelmesine neden olabilir ve bu da hepsini bir kez deneme yük dengelemesinin verimliliğini azaltır.</span><span class="sxs-lookup"><span data-stu-id="493d6-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="493d6-113">Bu davranış istense, bir <xref:System.ServiceModel.Channels.CustomBinding> veya Kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding> ile <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> özelliği kullanılarak sunucuda HTTP `Keep-Alive` devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="493d6-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="493d6-114">Aşağıdaki örnek, yapılandırma kullanarak bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="493d6-114">The following example shows how to do this using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service   
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"   
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="493d6-115">@No__t-0 ' da tanıtılan Basitleştirilmiş yapılandırmayı kullanarak, aşağıdaki Basitleştirilmiş yapılandırma kullanılarak aynı davranış yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="493d6-115">Using the simplified configuration introduced in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="493d6-116">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="493d6-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="493d6-117">WSHttp bağlaması ve WSDualHttp bağlaması ile yük dengeleme</span><span class="sxs-lookup"><span data-stu-id="493d6-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="493d6-118">@No__t-0 ve <xref:System.ServiceModel.WSDualHttpBinding>, varsayılan bağlama yapılandırmasında çeşitli değişiklikler yapıldığından, HTTP Yük Dengeleme teknikleri kullanılarak yük dengelenebilir.</span><span class="sxs-lookup"><span data-stu-id="493d6-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="493d6-119">Güvenlik bağlamı kurulumunu devre dışı bırak: Bu, <xref:System.ServiceModel.WSHttpBinding> ' deki <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliği `false` ' ye ayarlayarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="493d6-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="493d6-120">Alternatif olarak, güvenlik oturumları gerekliyse, [Güvenli Oturumlar](./feature-details/secure-sessions.md) konusunda açıklandığı gibi durum bilgisi olan güvenlik oturumları kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="493d6-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](./feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="493d6-121">Durum bilgisi olan güvenlik oturumları, güvenlik oturumunun tüm durumu koruma güvenlik belirtecinin bir parçası olarak her bir istekle birlikte aktarılcağından hizmetin durum bilgisiz kalmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="493d6-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="493d6-122">Durum bilgisi olan bir güvenlik oturumunu etkinleştirmek için, gerekli yapılandırma ayarları sistem tarafından sağlanmış <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> ' te gösterilmediğinden, <xref:System.ServiceModel.Channels.CustomBinding> veya Kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding> kullanılması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="493d6-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="493d6-123">Güvenilir oturumlar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="493d6-123">Do not use reliable sessions.</span></span> <span data-ttu-id="493d6-124">Bu özellik varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="493d6-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="493d6-125">Net. TCP bağlamasının yükünü dengeleme</span><span class="sxs-lookup"><span data-stu-id="493d6-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="493d6-126">@No__t-0, IP katmanı Yük Dengeleme teknikleri kullanılarak yük dengelenebilir.</span><span class="sxs-lookup"><span data-stu-id="493d6-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="493d6-127">Ancak <xref:System.ServiceModel.NetTcpBinding>, bağlantı gecikmesini azaltmak için varsayılan olarak TCP bağlantılarını havuzlar.</span><span class="sxs-lookup"><span data-stu-id="493d6-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="493d6-128">Bu, yük dengeleme için temel mekanizmayı kesintiye uğratan bir iyileştirmedir.</span><span class="sxs-lookup"><span data-stu-id="493d6-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="493d6-129">@No__t en iyi duruma getirme için birincil yapılandırma değeri, bağlantı havuzu ayarlarının bir parçası olan kiralama zaman aşımudur.</span><span class="sxs-lookup"><span data-stu-id="493d6-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="493d6-130">Bağlantı havuzu, istemci bağlantılarının gruptaki belirli sunucularla ilişkili olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="493d6-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="493d6-131">Bu bağlantıların yaşam süresi artdıkça (kira zaman aşımı ayarı tarafından denetlenen bir faktör), gruptaki çeşitli sunucular arasında yük dağılımı dengesiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="493d6-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="493d6-132">Sonuç olarak, ortalama çağrı süresi artar.</span><span class="sxs-lookup"><span data-stu-id="493d6-132">As a result the average call time increases.</span></span> <span data-ttu-id="493d6-133">Bu nedenle, yük dengeli senaryolarda <xref:System.ServiceModel.NetTcpBinding> kullanılırken, bağlama tarafından kullanılan varsayılan kira zaman aşımını azaltmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="493d6-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="493d6-134">30 saniyelik bir kira zaman aşımı, yük dengeli senaryolar için en iyi değer uygulamaya bağımlı olmasına rağmen makul bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="493d6-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="493d6-135">Kanal kiralama zaman aşımı ve diğer aktarım kotaları hakkında daha fazla bilgi için bkz. [Aktarım kotaları](./feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="493d6-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="493d6-136">Yük dengeli senaryolarda en iyi performansı elde etmek için <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> veya <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>) kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="493d6-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493d6-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="493d6-137">See also</span></span>

- [<span data-ttu-id="493d6-138">Internet Information Services Barındırma En İyi Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="493d6-138">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
