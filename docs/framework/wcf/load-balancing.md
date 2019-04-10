---
title: YükDengeleme
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: a43546b9cbb95cd16c1d94372e786acd103ea0bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228646"
---
# <a name="load-balancing"></a>YükDengeleme
Windows Communication Foundation (WCF) uygulamaları kapasitesini artırmak yollarından biri, bunları bir yük dengeli bir sunucu grubunda dağıtarak ölçeklendirme sağlamaktır. WCF uygulamaları, Windows Ağ Yükü Dengeleme gibi yazılım yük Dengeleyiciler gibi teknikler, standart yük dengelemeyi ve bunun yanı sıra donanım tabanlı Yük Dengeleme Gereçleri kullanarak Yük Dengeleme olabilir.  
  
 Aşağıdaki bölümlerde, çeşitli sistem tarafından sağlanan bağlamalar kullanılarak oluşturulan WCF uygulamaları yük dengelemeyi dikkate alınacak noktalar açıklanmaktadır.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Yük Dengeleme temel HTTP bağlama  
 Yük Dengeleme, kullanarak iletişim kuran bir WCF uygulamaları perspektifinden <xref:System.ServiceModel.BasicHttpBinding> hiç HTTP ortak diğer tür ağ trafiği (statik HTML içeriğini, ASP.NET sayfaları veya ASMX Web Hizmetleri) çok farklı değildir. Bu bağlamayı kullanan WCF kanalları, doğal olarak durum bilgisiz olduğundan ve kanal kapandığında kendi bağlantılarını sonlandırın. Bu nedenle, <xref:System.ServiceModel.BasicHttpBinding> teknikleri de var olan HTTP Yük Dengeleme ile çalışır.  
  
 Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> iletileri ile bir bağlantı HTTP üst bilgisi gönderir bir `Keep-Alive` bunları destekleyen hizmetler için kalıcı bağlantılar kurmanın istemcileri etkinleştiren değer. Bu yapılandırma, çünkü bağlantı aynı sunucuya sonraki ileti göndermek için yeniden kullanılabilir daha önce oluşturulan gelişmiş aktarım hızı sunar. Ancak, bağlantı yeniden hepsini bir kez deneme yük dengeleme işleminin verimliliğini azaltır yük dengeli grubu içindeki belirli bir sunucuya kesin ilişkili olmasını istemcilerin neden olabilir. Bu istenmeyen, davranıştır, HTTP `Keep-Alive` kullanılarak sunucuda devre dışı bırakılabilir <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> özelliğiyle bir <xref:System.ServiceModel.Channels.CustomBinding> veya kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding>. Aşağıdaki örnek Yapılandırması'nı kullanarak bunun nasıl yapılacağını gösterir.  
  
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
  
 Sürümünde Basitleştirilmiş yapılandırma kullanarak [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], aynı davranışı, aşağıdaki Basitleştirilmiş yapılandırma kullanılarak gerçekleştirilebilir.  
  
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
  
 Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>WSHttp bağlama ve WSDualHttp bağlama ile Yük Dengeleme  
 Hem <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> yapılandırma bağlama varsayılan birden fazla değişiklik yapılır sağlanan HTTP Yük Dengeleme teknikleri kullanarak yük dengeli.  
  
-   Güvenlik bağlamı kurma Kapat: Bu ayarı tarafından gerçekleştirilebilir <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliği <xref:System.ServiceModel.WSHttpBinding> için `false`. Güvenlik oturumu gerekliyse, alternatif olarak, bu durum bilgisi olan güvenlik oturumu açıklandığı kullanmak da mümkündür [güvenli oturumlar](../../../docs/framework/wcf/feature-details/secure-sessions.md) konu. Durum bilgisi olan güvenlik oturumu koruma güvenlik belirtecinin bir parçası olarak her bir istekle tüm durumları güvenlik oturumu için iletilen gibi durum bilgisiz kalmasına hizmetini etkinleştirin. Bir durum bilgisi olan güvenlik oturumu etkinleştirmek için bunu kullanmak için gerekli olduğunu unutmayın bir <xref:System.ServiceModel.Channels.CustomBinding> veya kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding> gerekli yapılandırma ayarlarını üzerinde gösterilmez <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> sistem tarafından sağlanır.  
  
-   Güvenilir oturumlar kullanmayın. Varsayılan olarak bu özelliği kapalıdır.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Yük Dengeleme Net.TCP bağlama  
 <xref:System.ServiceModel.NetTcpBinding> Yük dengeli IP-katman Yük Dengeleme teknikleri. Ancak, <xref:System.ServiceModel.NetTcpBinding> bağlantı gecikme süresini azaltmak için varsayılan olarak TCP bağlantı havuzları. Yük Dengeleme temel mekanizması uğratan iyileştirme budur. En iyi duruma getirmek için birincil yapılandırma değeri <xref:System.ServiceModel.NetTcpBinding> kiralama zaman aşımı, bağlantı havuzu ayarlarını bir parçasıdır. Bağlantı havuzu grubu içindeki belirli sunuculara ilişkili olmasını istemci bağlantıları neden olur. (Kiralama zaman aşımı ayarı tarafından denetlenen bir faktör) bu bağlantılar ömrünü artırmak, gruptaki çeşitli sunucular arasında yük dağıtımı dengesiz hale gelir. Sonuç olarak ortalama süresi arttıkça çağırın. Bunu kullanırken <xref:System.ServiceModel.NetTcpBinding> yük dengeli senaryolarda bağlama tarafından kullanılan varsayılan kiralama zaman aşımını azaltmayı göz önünde bulundurun. Uygulama bağımlı olsa da en iyi değeri 30 saniyelik kiralama zaman aşımı yük dengeli senaryoları için makul bir başlangıç noktası var. Kanal kiralama zaman aşımı ve diğer taşıma kotaları hakkında daha fazla bilgi için bkz. [taşıma kotaları](../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Yük dengeli senaryolarda en iyi performans için kullanmayı <xref:System.ServiceModel.NetTcpSecurity> (ya da <xref:System.ServiceModel.SecurityMode.Transport> veya <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Services Barındırma En İyi Uygulamaları](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
