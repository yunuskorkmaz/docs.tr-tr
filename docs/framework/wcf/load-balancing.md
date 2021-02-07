---
description: 'Daha fazla bilgi edinin: Yük Dengeleme'
title: YükDengeleme
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: 9f7946793fb9a9eec9baf531e4650f68b92151d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732819"
---
# <a name="load-balancing"></a><span data-ttu-id="c9d33-103">YükDengeleme</span><span class="sxs-lookup"><span data-stu-id="c9d33-103">Load Balancing</span></span>

<span data-ttu-id="c9d33-104">Windows Communication Foundation (WCF) uygulamalarının kapasitesini artırmanın bir yolu, bunları yük dengeli bir sunucu grubuna dağıtarak bunları ölçeklendirmektir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-104">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="c9d33-105">WCF uygulamaları, Windows Ağ Yükü Dengeleme gibi yazılım yük dengeleyiciler ve donanım tabanlı yük dengeleme gereçlerinin yanı sıra standart Yük Dengeleme teknikleri kullanılarak yük dengelenebilir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-105">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="c9d33-106">Aşağıdaki bölümlerde, sistem tarafından sunulan çeşitli bağlamalar kullanılarak oluşturulan yük dengeleme WCF uygulamalarına ilişkin konular ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9d33-106">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="c9d33-107">Temel HTTP bağlamasıyla Yük Dengeleme</span><span class="sxs-lookup"><span data-stu-id="c9d33-107">Load Balancing with the Basic HTTP Binding</span></span>  

 <span data-ttu-id="c9d33-108">Yük Dengeleme açısından, kullanılarak iletişim kuran WCF uygulamaları <xref:System.ServiceModel.BasicHttpBinding> diğer YAYGıN http ağ trafiği türlerinden (STATIK HTML içeriği, ASP.NET sayfaları veya asmx Web Hizmetleri) farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-108">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="c9d33-109">Bu bağlamayı kullanan WCF kanalları doğal olarak durum bilgisdir ve kanal kapandığında bağlantılarını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="c9d33-109">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="c9d33-110">Bu nedenle, <xref:System.ServiceModel.BasicHttpBinding> var olan HTTP Yük Dengeleme teknikleriyle iyi sonuç verir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-110">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="c9d33-111">Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> `Keep-Alive` istemcilerin bunları destekleyen hizmetlere kalıcı bağlantılar kurmasını sağlayan, bir değeri olan iletilerde BIR bağlantı http üst bilgisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-111">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="c9d33-112">Bu yapılandırma, daha önce oluşturulmuş bağlantılar daha sonraki iletileri aynı sunucuya göndermek için yeniden kullanılabilir olduğundan, gelişmiş aktarım hızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9d33-112">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="c9d33-113">Bununla birlikte, bağlantı yeniden kullanımı, istemcilerin yük dengeli gruptaki belirli bir sunucuyla kesin bir şekilde ilişkili hale gelmesine neden olabilir ve bu da hepsini bir kez deneme yük dengelemesinin verimliliğini azaltır.</span><span class="sxs-lookup"><span data-stu-id="c9d33-113">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="c9d33-114">Bu davranış istenmeyen ise, `Keep-Alive` <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> veya Kullanıcı tanımlı özelliği KULLANıLARAK sunucuda http devre dışı bırakılabilir <xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="c9d33-114">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="c9d33-115">Aşağıdaki örnek, yapılandırma kullanarak bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-115">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="c9d33-116">.NET Framework 4 ' te tanıtılan Basitleştirilmiş yapılandırmayı kullanarak, aşağıdaki Basitleştirilmiş yapılandırma kullanılarak aynı davranış yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-116">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="c9d33-117">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="c9d33-117">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="c9d33-118">WSHttp bağlaması ve WSDualHttp bağlaması ile yük dengeleme</span><span class="sxs-lookup"><span data-stu-id="c9d33-118">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  

 <span data-ttu-id="c9d33-119">Hem <xref:System.ServiceModel.WSHttpBinding> hem de, <xref:System.ServiceModel.WSDualHttpBinding> varsayılan bağlama yapılandırmasında çeşitli değişiklikler YAPıLDıĞıNDAN, HTTP Yük Dengeleme teknikleri kullanılarak yük dengelemesi yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-119">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="c9d33-120">Güvenlik bağlamı kurulmasını devre dışı bırakma veya durum bilgisi olan güvenlik oturumlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="c9d33-120">Turn off Security Context Establishment or use stateful security sessions.</span></span> <span data-ttu-id="c9d33-121">Üzerinde özelliği olarak ayarlanarak güvenlik bağlamı kurulması kapatılabilir <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> <xref:System.ServiceModel.WSHttpBinding> `false` .</span><span class="sxs-lookup"><span data-stu-id="c9d33-121">Security Context Establishment can be turned off by setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="c9d33-122">Kullanıyorsanız <xref:System.ServiceModel.WSDualHttpBinding> veya güvenlik oturumları gerekliyse, [güvenli oturumlarda](./feature-details/secure-sessions.md)açıklandığı gibi durum bilgisi olan güvenlik oturumları kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c9d33-122">If you are using <xref:System.ServiceModel.WSDualHttpBinding> or security sessions are required, it is possible to use stateful security sessions as described in [Secure Sessions](./feature-details/secure-sessions.md).</span></span> <span data-ttu-id="c9d33-123">Durum bilgisi olan güvenlik oturumları, güvenlik oturumunun tüm durumu koruma güvenlik belirtecinin bir parçası olarak her bir istekle birlikte aktarılcağından hizmetin durum bilgisiz kalmasına imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="c9d33-123">Stateful security sessions enable the service to remain stateless, as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="c9d33-124">Durum bilgisi olan bir güvenlik oturumunu etkinleştirmek için, <xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.Binding> gerekli yapılandırma ayarları sistem tarafından belirtilen ve üzerinde gösterilmediğinden, veya Kullanıcı tanımlı ' yı kullanmanız gerekir <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSDualHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="c9d33-124">To enable a stateful security session, you must use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>, as the necessary configuration settings are not exposed on the system-provided <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding>.</span></span>

- <span data-ttu-id="c9d33-125">Güvenlik bağlamı 'nı devre dışı bırakırsanız, hizmet kimlik bilgisi anlaşmasını de kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-125">If you turn off Security Context Establishment, you also need to turn off Service Credential Negotiation.</span></span> <span data-ttu-id="c9d33-126">Devre dışı bırakmak için <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential> özelliğini <xref:System.ServiceModel.WSHttpBinding> olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="c9d33-126">To turn it off, set the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="c9d33-127">Hizmet kimlik bilgisi anlaşmasını devre dışı bırakmak için, istemci üzerinde uç nokta kimliğini açıkça belirtmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-127">To disable Service Credential Negotiation, you may need to explicitly specify the endpoint identity on the client.</span></span>
  
- <span data-ttu-id="c9d33-128">Güvenilir oturumlar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="c9d33-128">Do not use reliable sessions.</span></span> <span data-ttu-id="c9d33-129">Bu özellik varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="c9d33-129">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="c9d33-130">Net. TCP bağlamasının yükünü dengeleme</span><span class="sxs-lookup"><span data-stu-id="c9d33-130">Load Balancing the Net.TCP Binding</span></span>  

 <span data-ttu-id="c9d33-131">, <xref:System.ServiceModel.NetTcpBinding> IP katmanı Yük Dengeleme teknikleri kullanılarak yük dengelenebilir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-131">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="c9d33-132">Ancak, <xref:System.ServiceModel.NetTcpBinding> bağlantı gecikmesini azaltmak için varsayılan olarak TCP bağlantısını havuzlar.</span><span class="sxs-lookup"><span data-stu-id="c9d33-132">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="c9d33-133">Bu, yük dengeleme için temel mekanizmayı kesintiye uğratan bir iyileştirmedir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-133">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="c9d33-134">İyileştirmek için birincil yapılandırma değeri, <xref:System.ServiceModel.NetTcpBinding> bağlantı havuzu ayarlarının bir parçası olan kiralama zaman aşımı ' dir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-134">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="c9d33-135">Bağlantı havuzu, istemci bağlantılarının gruptaki belirli sunucularla ilişkili olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c9d33-135">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="c9d33-136">Bu bağlantıların yaşam süresi artdıkça (kira zaman aşımı ayarı tarafından denetlenen bir faktör), gruptaki çeşitli sunucular arasında yük dağılımı dengesiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="c9d33-136">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="c9d33-137">Sonuç olarak, ortalama çağrı süresi artar.</span><span class="sxs-lookup"><span data-stu-id="c9d33-137">As a result the average call time increases.</span></span> <span data-ttu-id="c9d33-138">Bu nedenle, <xref:System.ServiceModel.NetTcpBinding> Yük dengeli senaryolarda kullanırken, bağlama tarafından kullanılan varsayılan kira zaman aşımını azaltmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c9d33-138">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="c9d33-139">30 saniyelik bir kira zaman aşımı, yük dengeli senaryolar için en iyi değer uygulamaya bağımlı olmasına rağmen makul bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="c9d33-139">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="c9d33-140">Kanal kiralama zaman aşımı ve diğer aktarım kotaları hakkında daha fazla bilgi için bkz. [Aktarım kotaları](./feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="c9d33-140">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="c9d33-141">Yük dengeli senaryolarda en iyi performansı elde etmek için (ya <xref:System.ServiceModel.NetTcpSecurity> da) kullanmayı düşünün <xref:System.ServiceModel.SecurityMode.Transport> <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="c9d33-141">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d33-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9d33-142">See also</span></span>

- [<span data-ttu-id="c9d33-143">Internet Information Services Barındırma En İyi Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="c9d33-143">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
