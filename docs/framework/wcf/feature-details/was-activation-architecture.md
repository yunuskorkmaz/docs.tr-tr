---
title: "WAS Etkinleştirme Mimarisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7563510fdd44336cb5f8c50705edefd732082347
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="was-activation-architecture"></a>WAS Etkinleştirme Mimarisi
Bu konuda maddeler halinde listelemektedir ve Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) bileşenlerinin açıklanır.  
  
## <a name="activation-components"></a>Etkinleştirme bileşenleri  
 OLAN birkaç mimari bileşenden oluşur:  
  
-   Dinleyici Bağdaştırıcısı yok. Belirli ağ protokollerine iletileri almak ve doğru çalışan işlemi için gelen iletileri yönlendirmek için WAS ile iletişim kuran Windows Hizmetleri.  
  
-   OLUŞTU. Oluşturulmasını ve yaşam çalışan işlemleri yöneten Windows hizmeti.  
  
-   Genel çalışan işlem yürütülebilir dosyası (w3wp.exe).  
  
-   Uygulama Yöneticisi. Oluşturulmasını ve yaşam süresini konak uygulamaların içinde çalışan işlem uygulama etki alanları yönetir.  
  
-   Protokol işleyici. Çalışan işlemde çalıştırın ve çalışan işlemin ve tek tek dinleyici bağdaştırıcısı arasındaki iletişimi yöneten protokole özgü bileşenleri. Protokol işleyici iki tür var: işlem protokol işleyici ve AppDomain protokol işleyici.  
  
 Olduğunda WAS bir çalışan işlem örneği etkinleştirir çalışan işlemine gerekli işlem protokol işleyici yükler ve uygulama barındırmak için uygulama etki alanı oluşturmak için uygulama Yöneticisi'ni kullanır. Uygulama etki alanı, uygulama kodunun yanı sıra uygulama iste tarafından kullanılan ağ protokolleri AppDomain protokol işleyici yükler.  
  
 ![MİMARİSİDİR](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")  
  
### <a name="listener-adapters"></a>Dinleyici Bağdaştırıcısı  
 Dinleyici Bağdaştırıcısı üzerinde dinleme ağ protokolünü kullanarak ileti almak için kullanılan ağ iletişimi mantığını uygulayan ayrı Windows hizmetleridir. Dinleyici Bağdaştırıcısı için aşağıdaki tabloda listelenmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protokoller.  
  
|Dinleyici Bağdaştırıcısı hizmet adı|Protokol|Notlar|  
|-----------------------------------|--------------|-----------|  
|W3SVC|http|HTTP etkinleştirmesi hem IIS 7.0 sağlayan ortak bileşeni ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].|  
|NetTcpActivator|net.tcp|NetTcpPortSharing hizmete bağlı.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|NET.MSMQ|İle kullanılmak üzere [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-tabanlı Message Queuing uygulamaları.|  
|NetMsmqActivator|MSMQ.FormatName|Geriye dönük uyumluluk varolan Message Queuing uygulamaları ile sağlar.|  
  
 Dinleyici Bağdaştırıcısı belirli protokoller için aşağıdaki XML örnekte gösterildiği gibi applicationHost.config dosyasında, yükleme sırasında kaydedilir.  
  
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
  
### <a name="protocol-handlers"></a>Protokol işleyici  
 İşlem ve AppDomain protokol işleyici belirli protokoller için makine düzeyinde Web.config dosyasına kaydedilir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WAS'ı WCF ile Kullanmak için Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
