---
title: '&lt;reliableSession&gt;'
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 0768cbce237b2d119be719eab1de9da4a551e5ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509811"
---
# <a name="ltreliablesessiongt"></a>&lt;reliableSession&gt;
WS-Reliable Mesajlaşma için ayarını tanımlar. Bu öğe için özel bir bağlama eklendiğinde, sonuçta elde edilen kanal tam olarak destekler-bir kez teslim Güvenceleri.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<reliableSession >  
  
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
|AcknowledgementInterval|A <xref:System.TimeSpan> kanal o noktaya kadar alınan iletileri bir bildirim göndermesini bekleyin geçmeye maksimum zaman aralığını içerir. 00:00:0.2 varsayılandır.|  
|FlowControlEnabled|Gelişmiş Akış denetiminin, WS-Reliable Mesajlaşma için akış denetimi Microsoft'a özel uygulanışı etkin olup olmadığını gösteren bir Boole değeri. Varsayılan, `true` değeridir.|  
|InactivityTimeout|A <xref:System.TimeSpan> herhangi bir ileti kanalı hatalı önce göndermemeyi diğer tarafın kanalı göndermemesini en uzun süreyi belirtir. Varsayılan değer 00:10:00 ' dir.<br /><br /> Bir kanalda etkinlik, bir uygulama ya da altyapı iletileri alma olarak tanımlanır. Bu özellik, etkin olmayan bir oturum etkin kalması için en uzun süreyi denetler. Daha uzun süre sahip etkinlik geçerse, oturum altyapısı ve kanal hataları tarafından iptal edildi. **Not:**  Uygulamayı düzenli aralıklarla bağlantının etkin kalması için ileti göndermek için gerekli değildir.|  
|MaxPendingChannels|En fazla bekleyebilen kabul edilecek bekleyebileceği kanal sayısını belirten bir tamsayı. Bu değer 1 için 16384 arasında kapsamlı olmalıdır. Varsayılan 4'tür.<br /><br /> Kanallar, ne zaman bunlar kabul zamanlanmayı bekleyen aşamasındadır. Bu sınıra ulaşıldığında, kanal yok oluşturulur. Bunun yerine, bunlar modu bu numara gelecek kadar aşağı (kanal kabul ederek) yerleştirilir. Bu bir Fabrika içi bir güvenlik sınırıdır.<br /><br /> Ne zaman eşiğine ulaşıldı ve yeni bir güvenilir oturum oluşturmak bir uzaktan uygulama çalıştığında, istek reddedilir ve bu hataların istenir açma işlemi. Bu sınır, giden kanallar bekleyen sayısı için geçerli değildir.|  
|MaxRetryCount|En fazla kaç kez belirten bir tamsayı güvenilir bir kanal için bir bildirim kendi altındaki bir kanalda Send çağırarak almadı bir ileti yeniden dener.<br /><br /> Bu değer, sıfırdan büyük olmalıdır. Varsayılan değer 8'dir.<br /><br /> Bu değer, sıfırdan büyük bir tamsayı olmalıdır. Bir bildirim son aktarım sonra kanal hataları alınmazsa.<br /><br /> Bir ileti, alıcıya teslim alıcı tarafından onaylanmış, aktarılacak olarak kabul edilir.<br /><br /> Bildirim zaman iletilmiş bir ileti için belirli bir süre içinde alınmadı, altyapı, ileti otomatik olarak geçer. Altyapı, en fazla kaç kez bu özelliği tarafından belirtilen ileti yeniden dener. Bir bildirim son aktarım sonra kanal hataları alınmazsa.<br /><br /> Altyapı üzerinde hesaplanan ortalama gidiş dönüş süresi almadığı ne zaman belirlemek için bir üstel geri alma algoritması kullanır. Süresi 1 saniye aktarım ve yaklaşık 8,5 ilk iletim girişimi ve son aktarım denemesini arasında geçen dakika cinsinden sonuçları her girişimi gecikmeyle Katlama önce başlangıçta başlar. İlk aktarım deneme süresi göre hesaplanan gidiş dönüş süresini ayarlanır ve bu girişimler geçirmesine süre elde edilen esnetme buna göre değişir. Bu aktarım süresini çeşitli ağ koşulları için dinamik olarak uyum sağlar.|  
|maxTransferWindowSize|En büyük arabellek boyutunu belirten bir tamsayı. Geçerli değerler 1 ile 4096 kapsamlı olmalı.<br /><br /> Bu öznitelik, istemcide henüz bir alıcı tarafından onaylanır iletileri tutmak için güvenilir bir kanal tarafından kullanılan arabelleğin en büyük boyutunu tanımlar. Bir ileti kotası birimidir. Arabelleği dolu ise, daha fazla gönderme işlemleri engellenir.<br /><br /> Bu öznitelik, bir alıcı ile kanal tarafından henüz uygulamaya gönderilen gelen iletileri depolamak için kullanılan arabelleğin en büyük boyutunu tanımlar. Arabelleği dolu ise, daha ayrıntılı iletiler sessizce alıcı tarafından bırakılır ve istemci tarafından aktarım gerektirir.|  
|ordered|İletilerin gönderildiği sırada ulşamasını garanti edilip edilmediğini belirten Boolean bir değer. Bu ayar `false`, iletileri sıralama dışında gelir. Varsayılan, `true` değeridir.|  
|ReliableMessagingVersion|Geçerli bir değer <xref:System.ServiceModel.ReliableMessagingVersion> kullanılacak WS-ReliableMessaging sürümünü belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenilir oturumlar güvenilir Mesajlaşma ve oturumları için özellikler sağlar. Güvenilir Mesajlaşma iletişimi hatasında yeniden deneme sayısı ve teslim Güvenceleri gibi sırayla varış belirtilmesi iletilerinin sağlar. Oturumlarının çağrıları arasında istemcilerin zachovat stav relace Bu öğe Ayrıca isteğe bağlı olarak sıralı mesaj teslimatı sağlar. Uygulanan bu oturum, SOAP ve aktarım aracılar çapraz.  
  
 Her bağlama öğesi gönderirken veya iletileri almak için bir işleme adımını temsil eder. Çalışma zamanında bağlama öğeleri kanal fabrikaları ve ileti göndermek ve almak için gereken gelen ve giden kanal yığınları oluşturmak gerekli olan bir dinleyici oluşturun. `reliableSession` Uç noktalar arasında güvenilir oturum oluşturmak ve bu oturum davranışını yapılandırma yığınında isteğe bağlı bir katmanı sağlar.  
  
 Daha fazla bilgi için [güvenilir oturumlar](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çeşitli taşıma ve istemci durumu korur ve sıralı teslim Güvenceleri belirten öğeleri kodlama, özellikle de güvenilir oturumlar etkinleştirme ileti özel bağlama yapılandırma gösterilmektedir. Bu özellik, uygulama yapılandırma dosyalarında istemci ve hizmet için yapılandırılır. Örnek, hizmet yapılandırmasını gösterir.  
  
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
- [Güvenilir Oturumlar](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
