---
title: WAS Etkinleştirme Mimarisi
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 77cebede5827016c5c9660663c0491614ba0ef19
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545988"
---
# <a name="was-activation-architecture"></a>WAS Etkinleştirme Mimarisi
Bu konu başlığı altında, Windows Işlem etkinleştirme hizmeti 'nin (WAS olarak da bilinir) bileşenleri ele alınmaktadır ve açıklanmaktadır.  
  
## <a name="activation-components"></a>Etkinleştirme bileşenleri  
 , Birkaç mimari bileşenden oluşur:  
  
- Dinleyici bağdaştırıcıları. Belirli ağ protokollerine ileti alan ve ile iletişim kuran Windows Hizmetleri, gelen iletileri doğru çalışan sürecine yönlendirmelidir.  
  
- Bulunamadı. Çalışan işlemlerinin oluşturulmasını ve yaşam süresini yöneten Windows hizmeti.  
  
- Genel çalışan işlemi yürütülebilir (w3wp.exe).  
  
- Uygulama Yöneticisi. Çalışan işlemi içinde uygulamaları barındıran uygulama etki alanlarının oluşturulmasını ve ömrünü yönetir.  
  
- Protokol işleyicileri. Çalışan işleminde çalışan ve çalışan işlem ile ayrı dinleyici bağdaştırıcıları arasındaki iletişimi yöneten protokole özgü bileşenler. İki tür protokol işleyicisi vardır: işlem protokol işleyicileri ve AppDomain protokol işleyicileri.  
  
 , Bir çalışan işlem örneğini etkinleştirdiğinde, çalışan işlemine gereken işlem protokol işleyicilerini yükler ve uygulamayı barındırmak üzere uygulama etki alanı oluşturmak için uygulama yöneticisini kullanır. Uygulama etki alanı, uygulamanın kodunun yanı sıra uygulama tarafından kullanılan ağ protokollerinin gerektirdiği AppDomain protokol işleyicilerini yükler.  
  
 ![WAS mimarisini gösteren ekran görüntüsü.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>Dinleyici bağdaştırıcıları  
 Dinleyici bağdaştırıcıları, dinleyeceği ağ protokolünü kullanarak ileti almak için kullanılan ağ iletişim mantığını uygulayan tek bir Windows hizmetidir. Aşağıdaki tabloda Windows Communication Foundation (WCF) protokolleri için dinleyici bağdaştırıcıları listelenmektedir.  
  
|Dinleyici bağdaştırıcısı hizmet adı|Protokol|Notlar|  
|-----------------------------------|--------------|-----------|  
|ÇALıŞTıRıN|http|Hem IIS 7,0 hem de WCF için HTTP etkinleştirmesi sağlayan ortak bileşen.|  
|Nettcpetkinleştirici|net.tcp|NetTcpPortSharing hizmetine bağlıdır.|  
|Netpipeetkinleştirici|net.pipe||  
|Netmsmqetkinleştirici|net. MSMQ|WCF tabanlı Message Queuing uygulamalarıyla kullanım için.|  
|Netmsmqetkinleştirici|MSMQ. formatname|Mevcut Message Queuing uygulamalarla geriye dönük uyumluluk sağlar.|  
  
 Belirli protokoller için dinleyici bağdaştırıcıları, aşağıdaki XML örneğinde gösterildiği gibi applicationHost.config dosyasına yükleme sırasında kaydedilir.  
  
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
  
### <a name="protocol-handlers"></a>Protokol Işleyicileri  
 Belirli protokoller için işlem ve AppDomain protokol işleyicileri makine düzeyinde Web.config dosyasına kaydedilir.  
  
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

- [WAS'ı WCF ile Kullanmak için Yapılandırma](configuring-the-wpa--service-for-use-with-wcf.md)
- [Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))
