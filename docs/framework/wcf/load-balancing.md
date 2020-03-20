---
title: Yük Dengeleme
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: a444df2b05803ec54c5bd9030ce12209cfe9bd07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183989"
---
# <a name="load-balancing"></a><span data-ttu-id="5f41c-102">Yük Dengeleme</span><span class="sxs-lookup"><span data-stu-id="5f41c-102">Load Balancing</span></span>
<span data-ttu-id="5f41c-103">Windows Communication Foundation (WCF) uygulamalarının kapasitesini artırmanın bir yolu, bunları yük dengeli bir sunucu çiftliğine yerleştirerek ölçeklendirmektir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="5f41c-104">WCF uygulamaları, Windows Network Load Balancing gibi yazılım yük dengeleyicileri ve donanım tabanlı yük dengeleme cihazları da dahil olmak üzere standart yük dengeleme teknikleri kullanılarak yük dengelenebilir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="5f41c-105">Aşağıdaki bölümlerde, sistem tarafından sağlanan çeşitli bağlamalar kullanılarak oluşturulmuş yük dengeleme WCF uygulamaları için dikkat edilmesi gereken hususlar tartışılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f41c-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="5f41c-106">Temel HTTP Bağlama ile Yük Dengeleme</span><span class="sxs-lookup"><span data-stu-id="5f41c-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="5f41c-107">Yük dengeleme açısından bakıldığında, bunları kullanarak iletişim sağlayan <xref:System.ServiceModel.BasicHttpBinding> WCF uygulamaları, diğer yaygın HTTP ağ trafiği türlerinden (statik HTML içeriği, ASP.NET sayfaları veya ASMX Web Hizmetleri) farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="5f41c-108">Bu bağlamayı kullanan WCF kanalları doğal olarak devlet değildir ve kanal kapandığında bağlantılarını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="5f41c-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="5f41c-109">Bu nedenle, <xref:System.ServiceModel.BasicHttpBinding> mevcut HTTP yük dengeleme teknikleri ile iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="5f41c-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="5f41c-110">Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> istemcilerin onları destekleyen hizmetlere `Keep-Alive` kalıcı bağlantılar kurmasını sağlayan, değerli iletilere bir bağlantı HTTP üstbilgisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="5f41c-111">Daha önce kurulmuş bağlantılar aynı sunucuya sonraki iletileri göndermek için yeniden kullanılabildiği için bu yapılandırma gelişmiş iş gücü sunar.</span><span class="sxs-lookup"><span data-stu-id="5f41c-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="5f41c-112">Ancak, bağlantı yeniden kullanımı istemcilerin yük dengeli çiftlikteki belirli bir sunucuyla güçlü bir şekilde ilişkilendirilmesine neden olabilir ve bu da yuvarlak-robin yük dengelemesinin etkinliğini azaltır.</span><span class="sxs-lookup"><span data-stu-id="5f41c-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="5f41c-113">Bu davranış `Keep-Alive` istenmiyorsa, HTTP özelliği ni <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> veya <xref:System.ServiceModel.Channels.CustomBinding> kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding>özelliği kullanarak sunucuda devre dışı bilebilir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="5f41c-114">Aşağıdaki örnek, yapılandırmayı kullanarak bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="5f41c-115">.NET Framework 4'te tanıtılan basitleştirilmiş yapılandırma kullanılarak, aynı davranış aşağıdaki basitleştirilmiş yapılandırma kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-115">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="5f41c-116">Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için wcf hizmetleri için [Basitleştirilmiş Yapılandırma](simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](./samples/simplified-configuration-for-wcf-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5f41c-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="5f41c-117">WSHttp Bağlama ve WSDualHttp Bağlama ile Yük Dengeleme</span><span class="sxs-lookup"><span data-stu-id="5f41c-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="5f41c-118"><xref:System.ServiceModel.WSHttpBinding> Hem de çeşitli değişiklikler varsayılan bağlama yapılandırması yapılır sayılsa bile HTTP yük dengeleme teknikleri kullanılarak yük dengeli <xref:System.ServiceModel.WSDualHttpBinding> olabilir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="5f41c-119">Güvenlik Bağlamı Kurulumu kapatın: Bu, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğin üzerinde <xref:System.ServiceModel.WSHttpBinding> ayarlanmasıyla `false`gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="5f41c-120">Alternatif olarak, güvenlik oturumları gerekiyorsa, [Güvenli Oturumlar](./feature-details/secure-sessions.md) konusunda açıklandığı gibi durumlu güvenlik oturumlarını kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5f41c-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](./feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="5f41c-121">Durumlu güvenlik oturumları, güvenlik oturumu için tüm devlet koruma güvenlik belirteci bir parçası olarak her istek ile iletilir gibi hizmetin devletsiz kalmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f41c-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="5f41c-122">Durum lu bir güvenlik oturumunu etkinleştirmek için, <xref:System.ServiceModel.Channels.CustomBinding> gerekli yapılandırma <xref:System.ServiceModel.Channels.Binding> ayarları açıklanmadığından <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> sistem tarafından sağlanan bir veya kullanıcı tarafından tanımlanan bir sözcük kullanılması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5f41c-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="5f41c-123">Güvenilir oturumlar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="5f41c-123">Do not use reliable sessions.</span></span> <span data-ttu-id="5f41c-124">Bu özellik varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f41c-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="5f41c-125">Net.TCP Bağlama yük dengeleme</span><span class="sxs-lookup"><span data-stu-id="5f41c-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="5f41c-126"><xref:System.ServiceModel.NetTcpBinding> IP katmanı yük dengeleme teknikleri kullanılarak yük dengeli olabilir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="5f41c-127">Ancak, <xref:System.ServiceModel.NetTcpBinding> bağlantı gecikmesini azaltmak için varsayılan olarak TCP bağlantılarını havuzları.</span><span class="sxs-lookup"><span data-stu-id="5f41c-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="5f41c-128">Bu, yük dengelemenin temel mekanizmasını engelleyen bir optimizasyondur.</span><span class="sxs-lookup"><span data-stu-id="5f41c-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="5f41c-129">En iyi duruma çıkarma nın <xref:System.ServiceModel.NetTcpBinding> birincil yapılandırma değeri, Bağlantı Havuzu Ayarları'nın bir parçası olan kira zaman ayarıdır.</span><span class="sxs-lookup"><span data-stu-id="5f41c-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="5f41c-130">Bağlantı birleştirme istemci bağlantılarının çiftlikteki belirli sunucularla ilişkilendirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="5f41c-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="5f41c-131">Bu bağlantıların ömrü arttıkça (kira zaman ayarı tarafından kontrol edilen bir faktör), çiftlikteki çeşitli sunucular arasındaki yük dağılımı dengesizleşir.</span><span class="sxs-lookup"><span data-stu-id="5f41c-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="5f41c-132">Sonuç olarak ortalama arama süresi artar.</span><span class="sxs-lookup"><span data-stu-id="5f41c-132">As a result the average call time increases.</span></span> <span data-ttu-id="5f41c-133">Bu nedenle, <xref:System.ServiceModel.NetTcpBinding> yük dengeli senaryoları kullanırken, bağlama tarafından kullanılan varsayılan kira zaman aşımını azaltmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="5f41c-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="5f41c-134">En uygun değer uygulamaya bağlı olsa da, 30 saniyelik kiralama zaman kaybı, yük dengeli senaryolar için makul bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="5f41c-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="5f41c-135">Kanal kiralama zaman aşımı ve diğer ulaşım kotaları hakkında daha fazla bilgi [için, Taşıma Kotaları'na](./feature-details/transport-quotas.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5f41c-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="5f41c-136">Yük dengeli senaryolarda en iyi performans <xref:System.ServiceModel.NetTcpSecurity> için, <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>(ya da) <xref:System.ServiceModel.SecurityMode.Transport> kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="5f41c-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f41c-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f41c-137">See also</span></span>

- [<span data-ttu-id="5f41c-138">Internet Information Services Barındırma En İyi Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="5f41c-138">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
