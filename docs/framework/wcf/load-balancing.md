---
title: YükDengeleme
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: 2a0644ea17db2923f5729feda40f3b2bff364231
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660755"
---
# <a name="load-balancing"></a><span data-ttu-id="36fde-102">YükDengeleme</span><span class="sxs-lookup"><span data-stu-id="36fde-102">Load Balancing</span></span>
<span data-ttu-id="36fde-103">Windows Communication Foundation (WCF) uygulamaları kapasitesini artırmak yollarından biri, bunları bir yük dengeli bir sunucu grubunda dağıtarak ölçeklendirme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="36fde-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="36fde-104">WCF uygulamaları, Windows Ağ Yükü Dengeleme gibi yazılım yük Dengeleyiciler gibi teknikler, standart yük dengelemeyi ve bunun yanı sıra donanım tabanlı Yük Dengeleme Gereçleri kullanarak Yük Dengeleme olabilir.</span><span class="sxs-lookup"><span data-stu-id="36fde-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="36fde-105">Aşağıdaki bölümlerde, çeşitli sistem tarafından sağlanan bağlamalar kullanılarak oluşturulan WCF uygulamaları yük dengelemeyi dikkate alınacak noktalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36fde-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="36fde-106">Yük Dengeleme temel HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="36fde-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="36fde-107">Yük Dengeleme, kullanarak iletişim kuran bir WCF uygulamaları perspektifinden <xref:System.ServiceModel.BasicHttpBinding> hiç HTTP ortak diğer tür ağ trafiği (statik HTML içeriğini, ASP.NET sayfaları veya ASMX Web Hizmetleri) çok farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="36fde-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="36fde-108">Bu bağlamayı kullanan WCF kanalları, doğal olarak durum bilgisiz olduğundan ve kanal kapandığında kendi bağlantılarını sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="36fde-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="36fde-109">Bu nedenle, <xref:System.ServiceModel.BasicHttpBinding> teknikleri de var olan HTTP Yük Dengeleme ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="36fde-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="36fde-110">Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> iletileri ile bir bağlantı HTTP üst bilgisi gönderir bir `Keep-Alive` bunları destekleyen hizmetler için kalıcı bağlantılar kurmanın istemcileri etkinleştiren değer.</span><span class="sxs-lookup"><span data-stu-id="36fde-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="36fde-111">Bu yapılandırma, çünkü bağlantı aynı sunucuya sonraki ileti göndermek için yeniden kullanılabilir daha önce oluşturulan gelişmiş aktarım hızı sunar.</span><span class="sxs-lookup"><span data-stu-id="36fde-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="36fde-112">Ancak, bağlantı yeniden hepsini bir kez deneme yük dengeleme işleminin verimliliğini azaltır yük dengeli grubu içindeki belirli bir sunucuya kesin ilişkili olmasını istemcilerin neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="36fde-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="36fde-113">Bu istenmeyen, davranıştır, HTTP `Keep-Alive` kullanılarak sunucuda devre dışı bırakılabilir <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> özelliğiyle bir <xref:System.ServiceModel.Channels.CustomBinding> veya kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="36fde-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="36fde-114">Aşağıdaki örnek Yapılandırması'nı kullanarak bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="36fde-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="36fde-115">Sürümünde Basitleştirilmiş yapılandırma kullanarak [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], aynı davranışı, aşağıdaki Basitleştirilmiş yapılandırma kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="36fde-115">Using the simplified configuration introduced in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="36fde-116">Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="36fde-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="36fde-117">WSHttp bağlama ve WSDualHttp bağlama ile Yük Dengeleme</span><span class="sxs-lookup"><span data-stu-id="36fde-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="36fde-118">Hem <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> yapılandırma bağlama varsayılan birden fazla değişiklik yapılır sağlanan HTTP Yük Dengeleme teknikleri kullanarak yük dengeli.</span><span class="sxs-lookup"><span data-stu-id="36fde-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
-   <span data-ttu-id="36fde-119">Güvenlik bağlamı kurma Kapat: Bu ayarı tarafından gerçekleştirilebilir <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliği <xref:System.ServiceModel.WSHttpBinding> için `false`.</span><span class="sxs-lookup"><span data-stu-id="36fde-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="36fde-120">Güvenlik oturumu gerekliyse, alternatif olarak, bu durum bilgisi olan güvenlik oturumu açıklandığı kullanmak da mümkündür [güvenli oturumlar](../../../docs/framework/wcf/feature-details/secure-sessions.md) konu.</span><span class="sxs-lookup"><span data-stu-id="36fde-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](../../../docs/framework/wcf/feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="36fde-121">Durum bilgisi olan güvenlik oturumu koruma güvenlik belirtecinin bir parçası olarak her bir istekle tüm durumları güvenlik oturumu için iletilen gibi durum bilgisiz kalmasına hizmetini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="36fde-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="36fde-122">Bir durum bilgisi olan güvenlik oturumu etkinleştirmek için bunu kullanmak için gerekli olduğunu unutmayın bir <xref:System.ServiceModel.Channels.CustomBinding> veya kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding> gerekli yapılandırma ayarlarını üzerinde gösterilmez <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> sistem tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="36fde-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
-   <span data-ttu-id="36fde-123">Güvenilir oturumlar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="36fde-123">Do not use reliable sessions.</span></span> <span data-ttu-id="36fde-124">Varsayılan olarak bu özelliği kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="36fde-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="36fde-125">Yük Dengeleme Net.TCP bağlama</span><span class="sxs-lookup"><span data-stu-id="36fde-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="36fde-126"><xref:System.ServiceModel.NetTcpBinding> Yük dengeli IP-katman Yük Dengeleme teknikleri.</span><span class="sxs-lookup"><span data-stu-id="36fde-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="36fde-127">Ancak, <xref:System.ServiceModel.NetTcpBinding> bağlantı gecikme süresini azaltmak için varsayılan olarak TCP bağlantı havuzları.</span><span class="sxs-lookup"><span data-stu-id="36fde-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="36fde-128">Yük Dengeleme temel mekanizması uğratan iyileştirme budur.</span><span class="sxs-lookup"><span data-stu-id="36fde-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="36fde-129">En iyi duruma getirmek için birincil yapılandırma değeri <xref:System.ServiceModel.NetTcpBinding> kiralama zaman aşımı, bağlantı havuzu ayarlarını bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="36fde-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="36fde-130">Bağlantı havuzu grubu içindeki belirli sunuculara ilişkili olmasını istemci bağlantıları neden olur.</span><span class="sxs-lookup"><span data-stu-id="36fde-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="36fde-131">(Kiralama zaman aşımı ayarı tarafından denetlenen bir faktör) bu bağlantılar ömrünü artırmak, gruptaki çeşitli sunucular arasında yük dağıtımı dengesiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="36fde-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="36fde-132">Sonuç olarak ortalama süresi arttıkça çağırın.</span><span class="sxs-lookup"><span data-stu-id="36fde-132">As a result the average call time increases.</span></span> <span data-ttu-id="36fde-133">Bunu kullanırken <xref:System.ServiceModel.NetTcpBinding> yük dengeli senaryolarda bağlama tarafından kullanılan varsayılan kiralama zaman aşımını azaltmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="36fde-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="36fde-134">Uygulama bağımlı olsa da en iyi değeri 30 saniyelik kiralama zaman aşımı yük dengeli senaryoları için makul bir başlangıç noktası var.</span><span class="sxs-lookup"><span data-stu-id="36fde-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="36fde-135">Kanal kiralama zaman aşımı ve diğer taşıma kotaları hakkında daha fazla bilgi için bkz. [taşıma kotaları](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="36fde-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="36fde-136">Yük dengeli senaryolarda en iyi performans için kullanmayı <xref:System.ServiceModel.NetTcpSecurity> (ya da <xref:System.ServiceModel.SecurityMode.Transport> veya <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="36fde-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36fde-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36fde-137">See also</span></span>
- [<span data-ttu-id="36fde-138">Internet Information Services Barındırma En İyi Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="36fde-138">Internet Information Services Hosting Best Practices</span></span>](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
