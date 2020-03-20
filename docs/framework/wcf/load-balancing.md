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
# <a name="load-balancing"></a>Yük Dengeleme
Windows Communication Foundation (WCF) uygulamalarının kapasitesini artırmanın bir yolu, bunları yük dengeli bir sunucu çiftliğine yerleştirerek ölçeklendirmektir. WCF uygulamaları, Windows Network Load Balancing gibi yazılım yük dengeleyicileri ve donanım tabanlı yük dengeleme cihazları da dahil olmak üzere standart yük dengeleme teknikleri kullanılarak yük dengelenebilir.  
  
 Aşağıdaki bölümlerde, sistem tarafından sağlanan çeşitli bağlamalar kullanılarak oluşturulmuş yük dengeleme WCF uygulamaları için dikkat edilmesi gereken hususlar tartışılmaktadır.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Temel HTTP Bağlama ile Yük Dengeleme  
 Yük dengeleme açısından bakıldığında, bunları kullanarak iletişim sağlayan <xref:System.ServiceModel.BasicHttpBinding> WCF uygulamaları, diğer yaygın HTTP ağ trafiği türlerinden (statik HTML içeriği, ASP.NET sayfaları veya ASMX Web Hizmetleri) farklı değildir. Bu bağlamayı kullanan WCF kanalları doğal olarak devlet değildir ve kanal kapandığında bağlantılarını sonlandırır. Bu nedenle, <xref:System.ServiceModel.BasicHttpBinding> mevcut HTTP yük dengeleme teknikleri ile iyi çalışır.  
  
 Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> istemcilerin onları destekleyen hizmetlere `Keep-Alive` kalıcı bağlantılar kurmasını sağlayan, değerli iletilere bir bağlantı HTTP üstbilgisi gönderir. Daha önce kurulmuş bağlantılar aynı sunucuya sonraki iletileri göndermek için yeniden kullanılabildiği için bu yapılandırma gelişmiş iş gücü sunar. Ancak, bağlantı yeniden kullanımı istemcilerin yük dengeli çiftlikteki belirli bir sunucuyla güçlü bir şekilde ilişkilendirilmesine neden olabilir ve bu da yuvarlak-robin yük dengelemesinin etkinliğini azaltır. Bu davranış `Keep-Alive` istenmiyorsa, HTTP özelliği ni <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> veya <xref:System.ServiceModel.Channels.CustomBinding> kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding>özelliği kullanarak sunucuda devre dışı bilebilir. Aşağıdaki örnek, yapılandırmayı kullanarak bunun nasıl yapılacağını gösterir.  
  
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
  
 .NET Framework 4'te tanıtılan basitleştirilmiş yapılandırma kullanılarak, aynı davranış aşağıdaki basitleştirilmiş yapılandırma kullanılarak gerçekleştirilebilir.  
  
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
  
 Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için wcf hizmetleri için [Basitleştirilmiş Yapılandırma](simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](./samples/simplified-configuration-for-wcf-services.md)bakın.  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>WSHttp Bağlama ve WSDualHttp Bağlama ile Yük Dengeleme  
 <xref:System.ServiceModel.WSHttpBinding> Hem de çeşitli değişiklikler varsayılan bağlama yapılandırması yapılır sayılsa bile HTTP yük dengeleme teknikleri kullanılarak yük dengeli <xref:System.ServiceModel.WSDualHttpBinding> olabilir.  
  
- Güvenlik Bağlamı Kurulumu kapatın: Bu, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğin üzerinde <xref:System.ServiceModel.WSHttpBinding> ayarlanmasıyla `false`gerçekleştirilebilir. Alternatif olarak, güvenlik oturumları gerekiyorsa, [Güvenli Oturumlar](./feature-details/secure-sessions.md) konusunda açıklandığı gibi durumlu güvenlik oturumlarını kullanmak mümkündür. Durumlu güvenlik oturumları, güvenlik oturumu için tüm devlet koruma güvenlik belirteci bir parçası olarak her istek ile iletilir gibi hizmetin devletsiz kalmasını sağlar. Durum lu bir güvenlik oturumunu etkinleştirmek için, <xref:System.ServiceModel.Channels.CustomBinding> gerekli yapılandırma <xref:System.ServiceModel.Channels.Binding> ayarları açıklanmadığından <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> sistem tarafından sağlanan bir veya kullanıcı tarafından tanımlanan bir sözcük kullanılması gerektiğini unutmayın.  
  
- Güvenilir oturumlar kullanmayın. Bu özellik varsayılan olarak kapalıdır.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Net.TCP Bağlama yük dengeleme  
 <xref:System.ServiceModel.NetTcpBinding> IP katmanı yük dengeleme teknikleri kullanılarak yük dengeli olabilir. Ancak, <xref:System.ServiceModel.NetTcpBinding> bağlantı gecikmesini azaltmak için varsayılan olarak TCP bağlantılarını havuzları. Bu, yük dengelemenin temel mekanizmasını engelleyen bir optimizasyondur. En iyi duruma çıkarma nın <xref:System.ServiceModel.NetTcpBinding> birincil yapılandırma değeri, Bağlantı Havuzu Ayarları'nın bir parçası olan kira zaman ayarıdır. Bağlantı birleştirme istemci bağlantılarının çiftlikteki belirli sunucularla ilişkilendirilmesine neden olur. Bu bağlantıların ömrü arttıkça (kira zaman ayarı tarafından kontrol edilen bir faktör), çiftlikteki çeşitli sunucular arasındaki yük dağılımı dengesizleşir. Sonuç olarak ortalama arama süresi artar. Bu nedenle, <xref:System.ServiceModel.NetTcpBinding> yük dengeli senaryoları kullanırken, bağlama tarafından kullanılan varsayılan kira zaman aşımını azaltmayı düşünün. En uygun değer uygulamaya bağlı olsa da, 30 saniyelik kiralama zaman kaybı, yük dengeli senaryolar için makul bir başlangıç noktasıdır. Kanal kiralama zaman aşımı ve diğer ulaşım kotaları hakkında daha fazla bilgi [için, Taşıma Kotaları'na](./feature-details/transport-quotas.md)bakın.  
  
 Yük dengeli senaryolarda en iyi performans <xref:System.ServiceModel.NetTcpSecurity> için, <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>(ya da) <xref:System.ServiceModel.SecurityMode.Transport> kullanmayı düşünün.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Services Barındırma En İyi Uygulamaları](./feature-details/internet-information-services-hosting-best-practices.md)
