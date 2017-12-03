---
title: '&lt;reliableSession&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f8484fe902b356f7fae4e526bdaa5610bf7d7ac6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltreliablesessiongt"></a>&lt;reliableSession&gt;
WS güvenilir Mesajlaşma ayarını tanımlar. Bu öğe için özel bağlama eklendiğinde, sonuçta elde edilen kanal tam olarak destekleyebilir-kere teslim Güvenceleri.  
  
 \<system.serviceModel >  
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
|acknowledgementInterval|A <xref:System.TimeSpan> kanal giderek bu noktaya kadar alınan iletileri bir bildirim göndermek için beklenecek en fazla zaman aralığını içerir. 00:00:0.2 varsayılandır.|  
|flowControlEnabled|Gelişmiş Akış denetimi, bir Microsoft özel uygulama WS güvenilir Mesajlaşma için akış denetimi etkin olup olmadığını gösteren bir Boole değeri. Varsayılan, `true` değeridir.|  
|InactivityTimeout|A <xref:System.TimeSpan> herhangi bir iletisi kanalı hatalı önce göndermemeyi diğer iletişim taraf kanal göndermemesini en uzun süreyi belirtir. Varsayılan değer 00:10: 00'dır.<br /><br /> Etkinlik kanalda bir uygulama veya altyapı iletileri alma olarak tanımlanır. Bu özellik, etkin olmayan oturumunu Canlı için en fazla süreyi denetler. Uzun süre hiç etkinlik geçerse, oturumun altyapı ve kanal hataları tarafından iptal edildi. **Not:** uygulamayı düzenli aralıklarla bağlantıyı canlı tut iletileri göndermek için gerekli değildir.|  
|maxPendingChannels|Kabul edilecek Dinleyicisi'ni bekleyebilirsiniz kanal maksimum sayısını belirten bir tamsayı. Bu değer, 1 değerini 16384 arasında (bunlar dahil) olmalıdır. Varsayılan değer 4'tür.<br /><br /> Kanallar, ne zaman oldukları kabul edilmesi için bekleyen bekleyen ' dir. Bu sınıra ulaşıldığında, hiçbir kanalı oluşturulur. Bunun yerine, bunlar modu bu numara gider kadar aşağı (kanalları kabul ederek) koyun. Bir Fabrika başına sınır budur.<br /><br /> Ne zaman eşiğine ulaşıldı ve yeni bir güvenilir oturumu uzak uygulama çalıştığında, istek reddedilir ve bu hataları istemde açık işlemi. Bu sınır, giden kanallar bekleyen sayısı için geçerli değildir.|  
|MaxRetryCount|En fazla kaç kez belirten bir tamsayı güvenilir bir kanal için bir bildirim gönderme temel kanalda çağırarak almadı bir ileti yeniden dener.<br /><br /> Bu değer sıfırdan büyük olmalıdır. Varsayılan 8'dir.<br /><br /> Bu değer sıfırdan büyük bir tamsayı olmalıdır. Bir bildirim son aktarım sonra kanal hataları alınmazsa.<br /><br /> Bir ileti alıcının kendi teslim alıcı tarafından onaylanan, aktarılacak olarak kabul edilir.<br /><br /> Bir bildirim süre iletilmiş bir ileti için belirli bir süre içinde alınmadı, altyapı ileti otomatik olarak geçer. Altyapı, en fazla kaç kez bu özelliği tarafından belirtilen iletiyi yeniden dener. Bir bildirim son aktarım sonra kanal hataları alınmazsa.<br /><br /> Altyapı hesaplanan bir ortalama gidiş dönüş zamanı temel alınarak yeniden ilettiği ne zaman belirlemek için bir üstel geri alma algoritma kullanır. Saat 1 saniye sırasında aktarım ve yaklaşık 8,5 ilk iletim girişimini ve son aktarım girişimi arasında geçen dakika cinsinden sonuçları her girişimi gecikmeyle Katlama önce başlangıçta başlatır. İlk aktarım girişimi yararlanma saatine göre hesaplanan gidiş dönüş süresini göre ve bu girişimler ele zaman ortaya çıkan esnetme buna göre değişir. Bu aktarım süresi dinamik olarak değişen ağ koşullarını uyum sağlar.|  
|maxTransferWindowSize|En büyük arabellek boyutunu belirten bir tamsayı. Geçerli değerler 1'den 4096 (bunlar dahil) arasındadır.<br /><br /> İstemcide, bu öznitelik henüz alıcı tarafından kabul edilen ileti tutmak için güvenilir bir kanal tarafından kullanılan arabellek en büyük boyutunu tanımlar. Bir ileti kota birimidir. Arabellek dolu olduğunda, başka gönderme işlemleri engellenir.<br /><br /> Alıcı, bu öznitelik kanal tarafından henüz uygulamaya gönderilen gelen iletileri depolamak için kullanılan arabelleğin en büyük boyutunu tanımlar. Arabellek dolu ise, daha ayrıntılı iletiler sessizce alıcı tarafından bırakılan ve istemci tarafından yeniden aktarım gerektirir.|  
|ordered|İletileri gönderildikleri sırayla gelmesi garanti edilip edilmeyeceğini belirten bir Boole değeri. Bu ayar ise `false`, iletileri sıralama dışında gelir. Varsayılan, `true` değeridir.|  
|reliableMessagingVersion|Geçerli bir değer <xref:System.ServiceModel.ReliableMessagingVersion> kullanılacak WS-ReliableMessaging sürümünü belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenilir oturumlar güvenilir Mesajlaşma ve oturumlar için özellikleri sağlar. Güvenilir Mesajlaşma iletişim başarısızlığı yeniden deneme ve teslim Güvenceleri gibi sıralı varış belirtilmesi iletilerinin sağlar. Oturum durumu çağrıları arasında istemcileri için korur. Bu öğe Ayrıca isteğe bağlı olarak sipariş edilen ileti teslimi sunar. Bu uygulanan oturum SOAP ve aktarım aracılar arası.  
  
 Her bağlama öğesi iletileri alırken veya gönderirken bir işleme adımı temsil eder. Çalışma zamanında kanal fabrikaları ve ileti gönderme ve alma için gereken gelen ve giden kanal yığınları oluşturmak gerekli olan dinleyicileri bağlama öğeleri oluşturun. `reliableSession` Uç noktalar arasında güvenilir oturum oluşturmak ve bu oturum davranışını yapılandırmak yığınında isteğe bağlı bir katmanı sağlar.  
  
 Daha fazla bilgi için bkz: [güvenilir oturumlar](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek özel bağlama çeşitli aktarım ve istemci durumunu korur ve sıralı teslim Güvenceleri belirtir öğeleri kodlama, özellikle güvenilir oturumlar etkinleştirme ileti ile nasıl yapılandırılacağını gösterir. Bu özellik uygulama yapılandırma dosyaları istemci ve hizmet için yapılandırılır. Örnek, hizmet yapılandırmasını gösterir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
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
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ReliableSessionElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>  
 [Güvenilir oturumlar](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
