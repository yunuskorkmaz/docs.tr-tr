---
title: WAS Etkinleştirme Mimarisi
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 2dd11ec9d642f5bfdd08c71487e82a8cb5133520
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557113"
---
# <a name="was-activation-architecture"></a>WAS Etkinleştirme Mimarisi
Bu konuda maddeler halinde listeler ve Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) bileşenlerinin açıklar.  
  
## <a name="activation-components"></a>Etkinleştirme bileşenleri  
 OLAN birkaç mimari bileşenden oluşur:  
  
-   Dinleyici bağdaştırıcıları. Belirli ağ protokollerine iletileri almak ve doğru alt işleme gelen iletileri yönlendirmek için WAS ile iletişim kuran Windows Hizmetleri.  
  
-   OLUŞTU. Oluşturulmasını ve alt işlemlerin yaşam süresini yöneten Windows hizmet.  
  
-   Genel çalışan işlemi (w3wp.exe) çalıştırılabilir.  
  
-   Uygulama Yöneticisi. Oluşturulmasını ve ana çalışan uygulamalardan işleyen bir uygulama etki alanları yaşam süresini yönetir.  
  
-   Protokol işleyiciler. Çalışan işlem içinde çalıştırın ve bir dinleyici bağdaştırıcıları ile çalışan işlemi arasındaki iletişimi yöneten protokole özgü bileşenler. Protokol işleyiciler iki tür vardır: işlem protokol işleyiciler ve AppDomain protokol işleyiciler.  
  
 Zaman WAS bir çalışan işlem örneği etkinleştirir, çalışan işlemin gerekli işlem protokol işleyiciler yükler ve uygulama Yöneticisi uygulamasını barındırmak için bir uygulama etki alanı oluşturmak için kullanır. Uygulama etki alanı, uygulama kodunun yanı sıra ağ protokolleri uygulama iste tarafından kullanılan AppDomain protokol işleyiciler yükler.  
  
 ![MİMARİSİDİR](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")  
  
### <a name="listener-adapters"></a>Dinleyici bağdaştırıcıları  
 Dinleyici, üzerinde dinleme ağ protokolünü kullanarak ileti almak için kullanılan ağ iletişimi mantığını uygulayan Windows Hizmetleri tek tek bağdaştırıcıdır. Aşağıdaki tabloda, Windows Communication Foundation (WCF) protokolleri için dinleyici bağdaştırıcıları listelenmektedir.  
  
|Dinleyici bağdaştırıcı hizmeti adı|Protokol|Notlar|  
|-----------------------------------|--------------|-----------|  
|W3SVC|http|IIS 7.0 hem de WCF için HTTP etkinleştirme sağlayan ortak bileşeni.|  
|NetTcpActivator|net.tcp|NetTcpPortSharing hizmete bağlıdır.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|net.msmq|Message Queuing WCF tabanlı uygulamaları ile kullanmak için.|  
|NetMsmqActivator|msmq.formatname|Geriye dönük uyumluluk Message Queuing var olan uygulamalarla birlikte sağlar.|  
  
 Dinleyici bağdaştırıcıları belirli protokoller için XML aşağıda gösterildiği gibi applicationHost.config dosyasında, yükleme sırasında kaydedilir.  
  
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
  
### <a name="protocol-handlers"></a>Protokol işleyiciler  
 İşlem ve AppDomain protokol işleyiciler belirli protokoller için makine düzeyinde Web.config dosyasına kaydedilir.  
  
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
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
