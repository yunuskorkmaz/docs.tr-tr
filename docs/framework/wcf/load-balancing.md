---
title: "YükDengeleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5874d7237608331e5d8284a4ad1cd94ba6fb3451
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="load-balancing"></a>YükDengeleme
Tek yönlü kapasitesini artırmak için [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulamaları bunları bir yük dengeli sunucu grubunda dağıtarak ölçeğini etmektir. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]uygulamalar, donanım tabanlı Yük Dengeleme cihazları yanı sıra, standart Yük Dengeleme yazılım yük dengeleyici gibi Windows Ağ Yükü Dengelemesi dahil olmak üzere teknikler kullanılarak Yük Dengeleme olabilir.  
  
 Aşağıdaki bölümlerde Yük Dengeleme konuları ele [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] çeşitli sistem tarafından sağlanan bağlamalar kullanılarak oluşturulan uygulamalar.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Yük Dengeleme ile temel HTTP bağlama  
 Yük Dengelemesi, açısından [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kullanarak iletişim kuran uygulamaları <xref:System.ServiceModel.BasicHttpBinding> HTTP ortak başka türlerde ağ trafiği (statik HTML içeriğini, ASP.NET sayfaları veya ASMX Web Hizmetleri) daha hiç farklı değildir. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Bu bağlamayı kullanan kanallar kendiliğinden durum bilgisiz ve kanal kapandığında kendi bağlantılarını sonlandırılacak. Bu nedenle, <xref:System.ServiceModel.BasicHttpBinding> teknikleri de var olan HTTP Yük Dengeleme ile çalışır.  
  
 Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> iletileri ile bir bağlantı HTTP üstbilgisi gönderir bir `Keep-Alive` bunları destekleyen hizmetler kalıcı bağlantı için istemcileri etkinleştirir değeri. Bu yapılandırma, bağlantıları aynı sunucuya sonraki ileti göndermek için yeniden kullanılabilir daha önce kurulmuş olduğundan Gelişmiş üretimi sunar. Ancak, bağlantı yeniden istemcilerin hepsini bir kez deneme yük dengeleme verimliliğini azaltır yük dengeli grubu içindeki belirli bir sunucuya kesinlikle ilişkili hale gelmesine neden olabilir. Bu davranış istenmeyen, ise HTTP `Keep-Alive` kullanarak sunucu üzerinde devre dışı bırakılabilir <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> özelliği ile bir <xref:System.ServiceModel.Channels.CustomBinding> veya kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding>. Aşağıdaki örnek Yapılandırması'nı kullanarak bunu kullanmayı gösterir.  
  
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
  
 Sürümünde sunulan Basitleştirilmiş Yapılandırması'nı kullanarak [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], aynı davranışı aşağıdaki Basitleştirilmiş yapılandırma kullanılarak gerçekleştirilebilir.  
  
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
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Varsayılan uç noktalar, bağlamaları ve davranışları, bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Yük Dengeleme WSHttp bağlama ve WSDualHttp bağlama  
 Hem <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> çeşitli değişiklikler yapılandırma bağlama varsayılan yapılan sağlanan HTTP Yük Dengeleme teknikler kullanılarak yük dengeli.  
  
-   Güvenlik bağlamı kurma devre dışı bırakma: Bu ayarı tarafından gerçekleştirilebilir <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliği <xref:System.ServiceModel.WSHttpBinding> için `false`. Güvenlik oturumları gerekliyse, alternatif olarak, bu durum bilgisi olan güvenlik oturumları açıklandığı gibi kullanmak da mümkündür [güvenli oturumlar](../../../docs/framework/wcf/feature-details/secure-sessions.md) konu. Durum bilgisi olan güvenlik oturumları koruma güvenlik belirtecinin bir parçası olarak her istek ile tüm güvenlik oturumu durumunun iletilen gibi durum bilgisiz kalmasına hizmetini etkinleştirin. Bir durum bilgisi olan güvenlik oturumu etkinleştirmek için bunu kullanmak için gerekli olduğuna dikkat edin bir <xref:System.ServiceModel.Channels.CustomBinding> veya kullanıcı tanımlı <xref:System.ServiceModel.Channels.Binding> gerekli yapılandırma ayarlarını üzerinde açık değildir <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSDualHttpBinding> sistem tarafından sağlanır.  
  
-   Güvenilir oturumlar kullanmayın. Bu özellik varsayılan olarak etkin değildir.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Yük Dengeleme Net.TCP bağlama  
 <xref:System.ServiceModel.NetTcpBinding> Yük dengeli IP katmanı Yük Dengeleme teknikleri. Ancak, <xref:System.ServiceModel.NetTcpBinding> bağlantı gecikmesini azaltmak için varsayılan olarak TCP bağlantılarını havuzları. Yük Dengelemesi temel mekanizmasını uğratan bir en iyi duruma getirme budur. En iyi duruma getirme için birincil yapılandırma değeri <xref:System.ServiceModel.NetTcpBinding> bağlantı havuzu ayarları parçası olan kira zaman aşımı. Bağlantı havuzu istemci bağlantılarını grubu içindeki belirli sunuculara ilişkili hale gelmesine neden olur. Bu bağlantıların yaşam süresi (kira zaman aşımı ayarı tarafından denetlenen bir faktör) artırın, gruptaki çeşitli sunucular arasında yük dağıtımı dengesiz haline gelir. Sonuç olarak ortalama süre artar çağırın. Kullanırken bunu <xref:System.ServiceModel.NetTcpBinding> yük dengeli senaryolarda, bağlama tarafından kullanılan varsayılan kira zaman aşımı azaltmayı göz önünde bulundurun. En iyi değeri uygulama bağımlı 30 saniyelik kira zaman aşımı yük dengeli senaryoları için makul bir başlangıç noktası olsa. Kanal kira zaman aşımı ve diğer taşıma kotaları hakkında daha fazla bilgi için bkz: [taşıma kotaları](../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Yük dengeli senaryolarda en iyi performans için kullanmayı <xref:System.ServiceModel.NetTcpSecurity> (ya da <xref:System.ServiceModel.SecurityMode.Transport> veya <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Internet Information Services Barındırma En İyi Uygulamaları](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
