---
title: YükDengeleme
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: c9d554dfd8d21b6e0e5f4aef0f4402e16485c2e8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="load-balancing"></a><span data-ttu-id="13ccc-102">YükDengeleme</span><span class="sxs-lookup"><span data-stu-id="13ccc-102">Load Balancing</span></span>
<span data-ttu-id="13ccc-103">Windows Communication Foundation (WCF) uygulamaları kapasitesini artırmak için bir bunları bir yük dengeli sunucu grubunda dağıtarak ölçeklendirmek için yoludur.</span><span class="sxs-lookup"><span data-stu-id="13ccc-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="13ccc-104">WCF uygulamaları teknikler, yazılım yük dengeleyici gibi Windows Ağ Yükü Dengelemesi dahil olmak üzere standart dengelemesini yanı sıra donanım tabanlı Yük Dengeleme cihazları kullanılarak Yük Dengeleme olabilir.</span><span class="sxs-lookup"><span data-stu-id="13ccc-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="13ccc-105">Aşağıdaki bölümlerde, Yük Dengeleme çeşitli sistem tarafından sağlanan bağlamalar kullanılarak oluşturulan WCF uygulamalar için konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13ccc-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="13ccc-106">Yük Dengeleme ile temel HTTP bağlama</span><span class="sxs-lookup"><span data-stu-id="13ccc-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="13ccc-107">Yük Dengeleme, kullanarak iletişim kuran WCF uygulamaları perspektifinden <xref:System.ServiceModel.BasicHttpBinding> HTTP ortak başka türlerde ağ trafiği (statik HTML içeriğini, ASP.NET sayfaları veya ASMX Web Hizmetleri) daha hiç farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="13ccc-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="13ccc-108">Bu bağlamayı kullanan WCF kanalları kendiliğinden durum bilgisiz ve kanal kapandığında kendi bağlantılarını sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="13ccc-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="13ccc-109">Bu nedenle, <xref:System.ServiceModel.BasicHttpBinding> teknikleri de var olan HTTP Yük Dengeleme ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="13ccc-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="13ccc-110">Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> iletileri ile bir bağlantı HTTP üstbilgisi gönderir bir `Keep-Alive` bunları destekleyen hizmetler kalıcı bağlantı için istemcileri etkinleştirir değeri.</span><span class="sxs-lookup"><span data-stu-id="13ccc-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="13ccc-111">Bu yapılandırma, bağlantıları aynı sunucuya sonraki ileti göndermek için yeniden kullanılabilir daha önce kurulmuş olduğundan Gelişmiş üretimi sunar.</span><span class="sxs-lookup"><span data-stu-id="13ccc-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="13ccc-112">Ancak, bağlantı yeniden istemcilerin hepsini bir kez deneme yük dengeleme verimliliğini azaltır yük dengeli grubu içindeki belirli bir sunucuya kesinlikle ilişkili hale gelmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="13ccc-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="13ccc-113">Bu davranış istenmeyen, ise HTTP `Keep-Alive` kullanarak sunucu üzerinde devre dışı bırakılabilir <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> özelliği ile bir <xref:System.ServiceModel.Channels.CustomBinding> veya kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="13ccc-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="13ccc-114">Aşağıdaki örnek Yapılandırması'nı kullanarak bunu kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="13ccc-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="13ccc-115">Sürümünde sunulan Basitleştirilmiş Yapılandırması'nı kullanarak [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], aynı davranışı aşağıdaki Basitleştirilmiş yapılandırma kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="13ccc-115">Using the simplified configuration introduced in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="13ccc-116">Varsayılan uç noktalar, bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="13ccc-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="13ccc-117">Yük Dengeleme WSHttp bağlama ve WSDualHttp bağlama</span><span class="sxs-lookup"><span data-stu-id="13ccc-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="13ccc-118">Hem <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> çeşitli değişiklikler yapılandırma bağlama varsayılan yapılan sağlanan HTTP Yük Dengeleme teknikler kullanılarak yük dengeli.</span><span class="sxs-lookup"><span data-stu-id="13ccc-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
-   <span data-ttu-id="13ccc-119">Güvenlik bağlamı kurma devre dışı bırakma: Bu ayarı tarafından gerçekleştirilebilir <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliği <xref:System.ServiceModel.WSHttpBinding> için `false`.</span><span class="sxs-lookup"><span data-stu-id="13ccc-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="13ccc-120">Güvenlik oturumları gerekliyse, alternatif olarak, bu durum bilgisi olan güvenlik oturumları açıklandığı gibi kullanmak da mümkündür [güvenli oturumlar](../../../docs/framework/wcf/feature-details/secure-sessions.md) konu.</span><span class="sxs-lookup"><span data-stu-id="13ccc-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](../../../docs/framework/wcf/feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="13ccc-121">Durum bilgisi olan güvenlik oturumları koruma güvenlik belirtecinin bir parçası olarak her istek ile tüm güvenlik oturumu durumunun iletilen gibi durum bilgisiz kalmasına hizmetini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="13ccc-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="13ccc-122">Bir durum bilgisi olan güvenlik oturumu etkinleştirmek için bunu kullanmak için gerekli olduğuna dikkat edin bir <xref:System.ServiceModel.Channels.CustomBinding> veya kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding> gerekli yapılandırma ayarlarını üzerinde açık değildir <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> sistem tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="13ccc-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
-   <span data-ttu-id="13ccc-123">Güvenilir oturumlar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="13ccc-123">Do not use reliable sessions.</span></span> <span data-ttu-id="13ccc-124">Bu özellik varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="13ccc-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="13ccc-125">Yük Dengeleme Net.TCP bağlama</span><span class="sxs-lookup"><span data-stu-id="13ccc-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="13ccc-126"><xref:System.ServiceModel.NetTcpBinding> Yük dengeli IP katmanı Yük Dengeleme teknikleri.</span><span class="sxs-lookup"><span data-stu-id="13ccc-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="13ccc-127">Ancak, <xref:System.ServiceModel.NetTcpBinding> bağlantı gecikmesini azaltmak için varsayılan olarak TCP bağlantılarını havuzları.</span><span class="sxs-lookup"><span data-stu-id="13ccc-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="13ccc-128">Yük Dengelemesi temel mekanizmasını uğratan bir en iyi duruma getirme budur.</span><span class="sxs-lookup"><span data-stu-id="13ccc-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="13ccc-129">En iyi duruma getirme için birincil yapılandırma değeri <xref:System.ServiceModel.NetTcpBinding> bağlantı havuzu ayarları parçası olan kira zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="13ccc-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="13ccc-130">Bağlantı havuzu istemci bağlantılarını grubu içindeki belirli sunuculara ilişkili hale gelmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="13ccc-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="13ccc-131">Bu bağlantıların yaşam süresi (kira zaman aşımı ayarı tarafından denetlenen bir faktör) artırın, gruptaki çeşitli sunucular arasında yük dağıtımı dengesiz haline gelir.</span><span class="sxs-lookup"><span data-stu-id="13ccc-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="13ccc-132">Sonuç olarak ortalama süre artar çağırın.</span><span class="sxs-lookup"><span data-stu-id="13ccc-132">As a result the average call time increases.</span></span> <span data-ttu-id="13ccc-133">Kullanırken bunu <xref:System.ServiceModel.NetTcpBinding> yük dengeli senaryolarda, bağlama tarafından kullanılan varsayılan kira zaman aşımı azaltmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="13ccc-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="13ccc-134">En iyi değeri uygulama bağımlı 30 saniyelik kira zaman aşımı yük dengeli senaryoları için makul bir başlangıç noktası olsa.</span><span class="sxs-lookup"><span data-stu-id="13ccc-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="13ccc-135">Kanal kira zaman aşımı ve diğer taşıma kotaları hakkında daha fazla bilgi için bkz: [taşıma kotaları](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="13ccc-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="13ccc-136">Yük dengeli senaryolarda en iyi performans için kullanmayı <xref:System.ServiceModel.NetTcpSecurity> (ya da <xref:System.ServiceModel.SecurityMode.Transport> veya <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="13ccc-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ccc-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13ccc-137">See Also</span></span>  
 [<span data-ttu-id="13ccc-138">Internet Information Services Barındırma En İyi Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="13ccc-138">Internet Information Services Hosting Best Practices</span></span>](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
