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
# <a name="load-balancing"></a>YükDengeleme

Windows Communication Foundation (WCF) uygulamalarının kapasitesini artırmanın bir yolu, bunları yük dengeli bir sunucu grubuna dağıtarak bunları ölçeklendirmektir. WCF uygulamaları, Windows Ağ Yükü Dengeleme gibi yazılım yük dengeleyiciler ve donanım tabanlı yük dengeleme gereçlerinin yanı sıra standart Yük Dengeleme teknikleri kullanılarak yük dengelenebilir.  
  
 Aşağıdaki bölümlerde, sistem tarafından sunulan çeşitli bağlamalar kullanılarak oluşturulan yük dengeleme WCF uygulamalarına ilişkin konular ele alınmaktadır.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Temel HTTP bağlamasıyla Yük Dengeleme  

 Yük Dengeleme açısından, kullanılarak iletişim kuran WCF uygulamaları <xref:System.ServiceModel.BasicHttpBinding> diğer YAYGıN http ağ trafiği türlerinden (STATIK HTML içeriği, ASP.NET sayfaları veya asmx Web Hizmetleri) farklı değildir. Bu bağlamayı kullanan WCF kanalları doğal olarak durum bilgisdir ve kanal kapandığında bağlantılarını sonlandırır. Bu nedenle, <xref:System.ServiceModel.BasicHttpBinding> var olan HTTP Yük Dengeleme teknikleriyle iyi sonuç verir.  
  
 Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> `Keep-Alive` istemcilerin bunları destekleyen hizmetlere kalıcı bağlantılar kurmasını sağlayan, bir değeri olan iletilerde BIR bağlantı http üst bilgisi gönderir. Bu yapılandırma, daha önce oluşturulmuş bağlantılar daha sonraki iletileri aynı sunucuya göndermek için yeniden kullanılabilir olduğundan, gelişmiş aktarım hızı sağlar. Bununla birlikte, bağlantı yeniden kullanımı, istemcilerin yük dengeli gruptaki belirli bir sunucuyla kesin bir şekilde ilişkili hale gelmesine neden olabilir ve bu da hepsini bir kez deneme yük dengelemesinin verimliliğini azaltır. Bu davranış istenmeyen ise, `Keep-Alive` <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> veya Kullanıcı tanımlı özelliği KULLANıLARAK sunucuda http devre dışı bırakılabilir <xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.Binding> . Aşağıdaki örnek, yapılandırma kullanarak bunun nasıl yapılacağını gösterir.  
  
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
  
 .NET Framework 4 ' te tanıtılan Basitleştirilmiş yapılandırmayı kullanarak, aşağıdaki Basitleştirilmiş yapılandırma kullanılarak aynı davranış yapılabilir.  
  
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
  
 Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>WSHttp bağlaması ve WSDualHttp bağlaması ile yük dengeleme  

 Hem <xref:System.ServiceModel.WSHttpBinding> hem de, <xref:System.ServiceModel.WSDualHttpBinding> varsayılan bağlama yapılandırmasında çeşitli değişiklikler YAPıLDıĞıNDAN, HTTP Yük Dengeleme teknikleri kullanılarak yük dengelemesi yapılabilir.  
  
- Güvenlik bağlamı kurulmasını devre dışı bırakma veya durum bilgisi olan güvenlik oturumlarını kullanma. Üzerinde özelliği olarak ayarlanarak güvenlik bağlamı kurulması kapatılabilir <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> <xref:System.ServiceModel.WSHttpBinding> `false` . Kullanıyorsanız <xref:System.ServiceModel.WSDualHttpBinding> veya güvenlik oturumları gerekliyse, [güvenli oturumlarda](./feature-details/secure-sessions.md)açıklandığı gibi durum bilgisi olan güvenlik oturumları kullanmak mümkündür. Durum bilgisi olan güvenlik oturumları, güvenlik oturumunun tüm durumu koruma güvenlik belirtecinin bir parçası olarak her bir istekle birlikte aktarılcağından hizmetin durum bilgisiz kalmasına imkan tanır. Durum bilgisi olan bir güvenlik oturumunu etkinleştirmek için, <xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.Binding> gerekli yapılandırma ayarları sistem tarafından belirtilen ve üzerinde gösterilmediğinden, veya Kullanıcı tanımlı ' yı kullanmanız gerekir <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSDualHttpBinding> .

- Güvenlik bağlamı 'nı devre dışı bırakırsanız, hizmet kimlik bilgisi anlaşmasını de kapatmanız gerekir. Devre dışı bırakmak için <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential> özelliğini <xref:System.ServiceModel.WSHttpBinding> olarak ayarlayın `false` . Hizmet kimlik bilgisi anlaşmasını devre dışı bırakmak için, istemci üzerinde uç nokta kimliğini açıkça belirtmeniz gerekebilir.
  
- Güvenilir oturumlar kullanmayın. Bu özellik varsayılan olarak kapalıdır.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Net. TCP bağlamasının yükünü dengeleme  

 , <xref:System.ServiceModel.NetTcpBinding> IP katmanı Yük Dengeleme teknikleri kullanılarak yük dengelenebilir. Ancak, <xref:System.ServiceModel.NetTcpBinding> bağlantı gecikmesini azaltmak için varsayılan olarak TCP bağlantısını havuzlar. Bu, yük dengeleme için temel mekanizmayı kesintiye uğratan bir iyileştirmedir. İyileştirmek için birincil yapılandırma değeri, <xref:System.ServiceModel.NetTcpBinding> bağlantı havuzu ayarlarının bir parçası olan kiralama zaman aşımı ' dir. Bağlantı havuzu, istemci bağlantılarının gruptaki belirli sunucularla ilişkili olmasına neden olur. Bu bağlantıların yaşam süresi artdıkça (kira zaman aşımı ayarı tarafından denetlenen bir faktör), gruptaki çeşitli sunucular arasında yük dağılımı dengesiz hale gelir. Sonuç olarak, ortalama çağrı süresi artar. Bu nedenle, <xref:System.ServiceModel.NetTcpBinding> Yük dengeli senaryolarda kullanırken, bağlama tarafından kullanılan varsayılan kira zaman aşımını azaltmayı göz önünde bulundurun. 30 saniyelik bir kira zaman aşımı, yük dengeli senaryolar için en iyi değer uygulamaya bağımlı olmasına rağmen makul bir başlangıç noktasıdır. Kanal kiralama zaman aşımı ve diğer aktarım kotaları hakkında daha fazla bilgi için bkz. [Aktarım kotaları](./feature-details/transport-quotas.md).  
  
 Yük dengeli senaryolarda en iyi performansı elde etmek için (ya <xref:System.ServiceModel.NetTcpSecurity> da) kullanmayı düşünün <xref:System.ServiceModel.SecurityMode.Transport> <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Services Barındırma En İyi Uygulamaları](./feature-details/internet-information-services-hosting-best-practices.md)
