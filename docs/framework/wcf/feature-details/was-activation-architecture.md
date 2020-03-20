---
title: WAS Etkinleştirme Mimarisi
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 67ddcd97ac75ddeb0765c38bb9ce7b5e8f039272
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184246"
---
# <a name="was-activation-architecture"></a>WAS Etkinleştirme Mimarisi
Bu konu, Windows Process Etkinleştirme Hizmeti'nin (WAS olarak da bilinir) bileşenlerini ayrıntılı olarak bildirir ve tartışır.  
  
## <a name="activation-components"></a>Etkinleştirme Bileşenleri  
 WAS çeşitli mimari bileşenlerden oluşur:  
  
- Dinleyici adaptörleri. Belirli ağ protokollerinde ileti alan ve gelen iletileri doğru alt işleme yönlendirmek için WAS ile iletişim sağlayan Windows hizmetleri.  
  
- ÖYLEYDI. Alt işlemlerin oluşturulmasını ve kullanım ömrünü yöneten Windows hizmeti.  
  
- Genel alt işlem çalıştırılabilir (w3wp.exe).  
  
- Başvuru yöneticisi. Alt işlem içinde uygulamaları barındıran uygulama etki alanlarının oluşturulmasını ve kullanım ömrünü yönetir.  
  
- Protokol işleyicileri. Alt işlemde çalışan ve alt işlem ile tek tek dinleyici bağdaştırıcıları arasındaki iletişimi yöneten protokole özgü bileşenler. İki tür iletişim kuralı işleyicisi vardır: işlem protokolü işleyicileri ve AppDomain iletişim kuralı işleyicileri.  
  
 WAS bir alt işlem örneğini etkinleştirdiğinde, gerekli işlem protokolü işleyicilerini alt işleme yükler ve uygulamayı barındıracak bir uygulama etki alanı oluşturmak için uygulama yöneticisini kullanır. Uygulama etki alanı, uygulamanın kodunu ve uygulama tarafından kullanılan ağ protokollerinin gerektirdiği AppDomain protokol işleyicilerini yükler.  
  
 ![WAS mimarisini gösteren ekran görüntüsü.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>Dinleyici Adaptörleri  
 Dinleyici bağdaştırıcıları, dinledikleri ağ iletişimini kullanarak ileti leri almak için kullanılan ağ iletişimi mantığını uygulayan tek tek Windows hizmetleridir. Aşağıdaki tabloda Windows Communication Foundation (WCF) protokolleri için dinleyici bağdaştırıcıları listelenir.  
  
|Dinleyici bağdaştırıcı hizmet adı|Protokol|Notlar|  
|-----------------------------------|--------------|-----------|  
|W3svc|http|Hem IIS 7.0 hem de WCF için HTTP etkinleştirme sağlayan ortak bileşen.|  
|NetTcpActivator|net.tcp|NetTcpPortSharing hizmetine bağlıdır.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|net.msmq|WCF tabanlı İleti Sıraya uygulamaları ile kullanım için.|  
|NetMsmqActivator|msmq.formatname|Varolan İleti Sıralaması uygulamalarıyla geriye dönük uyumluluk sağlar.|  
  
 Belirli protokoller için dinleyici bağdaştırıcıları aşağıdaki XML örneğinde gösterildiği gibi applicationHost.config dosyasında yükleme sırasında kaydedilir.  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a>Protokol Handleyicileri  
 Belirli protokoller için Işlem ve AppDomain protokol işleyicileri makine düzeyinde Web.config dosyasında kaydedilir.  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WAS'ı WCF ile Kullanmak için Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Windows Server App Kumaş Barındırma Özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
