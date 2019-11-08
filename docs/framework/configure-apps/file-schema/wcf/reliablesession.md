---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 95f6646041dc2dd7bae7691a0a9f748c844f50b6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738753"
---
# <a name="reliablesession"></a>Reliableoturum > \<
WS-güvenilir mesajlaşma için ayarı tanımlar. Bu öğe özel bir bağlamaya eklendiğinde, elde edilen kanal, tam olarak bir kez teslimat hakkı destekleyebilir.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<reliableSession >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"
                 flowControlEnabled="Boolean"
                 inactivityTimeout="TimeSpan"
                 maxPendingChannels="Integer"
                 maxRetryCount="Integer"
                 maxTransferWindowSize="Integer"
                 reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"
                 ordered="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|bildiren Gementınterval|Kanalın bu noktaya kadar alınan iletiler için bildirim göndermek üzere bekleyeceği maksimum zaman aralığını içeren bir <xref:System.TimeSpan>. Varsayılan değer 00:00:0.2 ' dir.|  
|flowControlEnabled|Gelişmiş akış denetiminin, WS-güvenilir mesajlaşma için Microsoft 'a özgü akış denetimi uygulamasının etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer. Varsayılan, `true` değeridir.|  
|InactivityTimeout|Kanalın, diğer iletişim tarafına, kanalı hatalı olmadan önce hiçbir ileti gönderemediğinden izin veren en uzun süreyi belirten <xref:System.TimeSpan>. Varsayılan değer 00:10:00 ' dir.<br /><br /> Bir kanaldaki etkinlik, uygulama veya altyapı iletileri alma olarak tanımlanır. Bu özellik, etkin olmayan bir oturumun etkin tutulması için en uzun süreyi denetler. Daha uzun süre hiçbir etkinlik olmadan geçerse, oturum altyapı ve kanal hataları tarafından iptal edilir. **Note:**  Uygulamanın bağlantıyı canlı tutmak için düzenli olarak ileti gönderebilmesi gerekli değildir.|  
|maxPendingChannels|Dinleyicide bekleyebilen en fazla kanal sayısını belirten bir tamsayı. Bu değer 1 ila 16384 arasında olmalıdır. Varsayılan değer 4 ' dir.<br /><br /> Kanallar kabul edilmeden önce bekliyor. Bu sınıra ulaşıldığında, hiçbir kanal oluşturulmaz. Bunun yerine, bu sayı kapatılıncaya kadar (bekleyen kanalları kabul ederek) bekleyen moda konur. Bu, fabrika başına bir limit.<br /><br /> Eşiğe ulaşıldığında ve bir uzak uygulama yeni bir güvenilir oturum kurmaya çalıştığında, istek reddedilir ve bu hataları isteyen açma işlemi yapılır. Bu sınır, bekleyen giden kanalların sayısı için geçerlidir.|  
|maxRetryCount|Güvenilir bir kanalın, temel aldığı kanalda Gönder ' i çağırarak bildirim almamış bir iletiyi yeniden göndermek için yaptığı deneme sayısının üst sınırını belirten bir tamsayı.<br /><br /> Bu değer sıfırdan büyük olmalıdır. Varsayılan değer 8 ' dir.<br /><br /> Bu değer sıfırdan büyük bir tamsayı olmalıdır. Son yeniden iletim sonrasında bir bildirim alınmıyorsa, kanal hataları.<br /><br /> Alıcı tarafından alıcının teslimatı onaylanmışsa bir ileti aktarıldıkları kabul edilir.<br /><br /> Bir bildirim, iletilen bir ileti için belirli bir süre içinde alınmadığında, altyapı iletiyi otomatik olarak yeniden iletir. Altyapı, bu özellik tarafından belirtilen en fazla kaç kez iletiyi yeniden göndermeye çalışır. Son yeniden iletim sonrasında bir bildirim alınmıyorsa, kanal hataları.<br /><br /> Altyapı, hesaplanan ortalama gidiş dönüş zamanına bağlı olarak ne zaman yeniden aktarım için bir üstel geri dönüş algoritması kullanır. İlk iletim denemesi ve son yeniden iletme girişimi arasında yaklaşık 8,5 dakika boyunca yeniden iletimden önce 1 saniye içinde başlar ve her denemede gecikme süresi ikiye geçer. İlk yeniden iletim denemesinin saati, hesaplanan gidiş dönüş zamanına ve bu girişimlere göre farklılık gösteren elde edilen süre uzatılmasına göre düzeltilir. Bu, yeniden aktarım süresinin farklı ağ koşullarına dinamik olarak uyum sağlamasına izin verir.|  
|maxTransferWindowSize|Arabelleğin en büyük boyutunu belirten bir tamsayı. Geçerli değerler 1 ile 4096 arasında olmalıdır.<br /><br /> İstemcide, bu öznitelik, alıcı tarafından henüz onaylanmayan iletileri tutmak için güvenilir bir kanal tarafından kullanılan arabelleğin en büyük boyutunu tanımlar. Kota birimi bir iletidir. Arabellek doluysa, daha fazla gönderme işlemi engellenir.<br /><br /> Alıcıda, bu öznitelik kanal tarafından henüz uygulamaya dağıtılan gelen iletileri depolamak için kullanılan arabelleğin en büyük boyutunu tanımlar. Arabellek doluysa, daha fazla ileti alıcı tarafından sessizce bırakılır ve istemci tarafından yeniden aktarım gerektirir.|  
|ordered|İletilerin gönderildikleri sırada gelmesi garanti edilip edilmeyeceğini belirten bir Boole değeri. Bu ayar `false`, iletiler sırayla gelebilir. Varsayılan, `true` değeridir.|  
|Belirten ReliableMessagingVersion|Kullanılacak WS-ReliableMessaging sürümünü belirten <xref:System.ServiceModel.ReliableMessagingVersion> geçerli bir değer.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\< bağlama >](bindings.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenilir Oturumlar, güvenilir mesajlaşma ve oturumlara yönelik özellikler sağlar. Güvenilir Mesajlaşma, hata durumunda iletişim kurmayı yeniden dener ve iletilerin belirli bir sırada gönderilmesini sağlar. Oturumlar, çağrılar arasındaki istemciler için durumu korur. Bu öğe Ayrıca isteğe bağlı olarak sıralı ileti teslimi sağlar. Bu uygulanan oturum, SOAP ve aktarım aracıları arası olabilir.  
  
 Her bağlama öğesi ileti gönderirken veya alırken bir işleme adımını temsil eder. Çalışma zamanında, bağlama öğeleri, ileti göndermek ve almak için gereken giden ve gelen kanal yığınları oluşturmak için gereken kanal fabrikalarını ve dinleyicileri oluşturur. `reliableSession`, uç noktalar arasında güvenilir bir oturum kurabilen ve bu oturumun davranışını yapılandırasağlayan yığında isteğe bağlı bir katman sağlar.  
  
 Daha fazla bilgi için bkz. [Güvenilir Oturumlar](../../../wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel bir bağlamanın çeşitli taşıma ve ileti kodlama öğeleriyle nasıl yapılandırılacağını gösterir, özellikle de istemci durumunu tutan ve sipariş içi teslim bildirimlerini belirten güvenilir oturumları etkinleştirir. Bu özellik, istemci ve hizmet için uygulama yapılandırma dosyalarında yapılandırılır. Örnek, hizmet yapılandırmasını gösterir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [Güvenilir Oturumlar](../../../wcf/feature-details/reliable-sessions.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
