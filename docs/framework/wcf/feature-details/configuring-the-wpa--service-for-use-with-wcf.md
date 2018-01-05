---
title: "Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12df9e3760774b4dc8d4e8f73a09df5e79c2453e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma
Bu konuda, Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) için gerekli adımlar açıklanmaktadır [!INCLUDE[wv](../../../../includes/wv-md.md)] ana bilgisayara [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ağ protokolleri HTTP üzerinden iletişim kurmazlar Hizmetleri. Aşağıdaki bölümlerde bu yapılandırma için adımlar verilmiştir:  
  
-   Yükleme (veya yüklemesini onaylamak) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] etkinleştirme bileşenleri gereklidir.  
  
-   Kullanmak istediğiniz ağ protokolü bağlamaları ile WAS site oluşturun veya varolan bir site için yeni bir protokol bağlama ekleyin.  
  
-   Hizmetlerinizin barındırmak ve gerekli ağ protokolleri kullanmak bu uygulamayı etkinleştirmek için bir uygulama oluşturun.  
  
-   Derleme bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti bir HTTP olmayan uç noktasını kullanıma sunar.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Bir Site ile HTTP olmayan bağlamaları yapılandırma  
 Bir HTTP olmayan bağlama WAS ile kullanmak için site bağlaması için WAS yapılandırma eklenmesi gerekir. WAS yapılandırma deposu %windir%\system32\inetsrv\config dizininde bulunan applicationHost.config dosyasıdır. Bu yapılandırma deposu WAS ve IIS 7.0 tarafından paylaşılır.  
  
 applicationHost.config herhangi bir standart metin düzenleyicisi (Not Defteri gibi) ile açılmış bir XML metin dosyasıdır. Ancak, [!INCLUDE[iisver](../../../../includes/iisver-md.md)] komut satırı yapılandırma aracını (appcmd.exe) olan HTTP olmayan site bağlamaları eklemek için tercih edilen yol.  
  
 Aşağıdaki komutu (Bu komutu tek bir satır olarak girilir) appcmd.exe kullanarak varsayılan Web sitesi net.tcp site bağlaması ekler.  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Bu komut, aşağıda applicationHost.config dosyasında belirtilen satırı ekleyerek, varsayılan Web sitesine yeni net.tcp bağlama ekler.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>HTTP olmayan protokolleri kullanmak üzere bir uygulama etkinleştirme  
 Etkinleştirmek veya tek tek ağ protocolsat uygulama düzeyinde devre dışı bırakabilirsiniz. Aşağıdaki komut, çalışan bir uygulama için hem HTTP hem de net.tcp protokollerini etkinleştirmek verilmektedir `Default Web Site`.  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Etkin protokoller listesinde de ayarlanabilir \<applicationDefaults > ApplicationHost.config dosyasında depolanan sitenin XML yapılandırma öğesidir.  
  
 Aşağıdaki XML kodunu applicationHost.config öğesinden hem HTTP hem de HTTP olmayan protokolleri bağlı bir site gösterilmektedir. HTTP olmayan protokolleri desteklemek için gereken ek yapılandırma yorumlarla belirtilmiştir.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
    <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
    </application>  
       <bindings>  
            //The following two lines are added by the command.  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile   
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging   
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults   
      applicationPool="DefaultAppPool"   
      //The following line is inserted by the command.  
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 Aşağıdaki hata için HTTP olmayan etkinleştirme WAS kullanarak bir hizmet etkinleştirmeyi dener ve yüklenmediğinde veya WAS yapılandırılmış görebilirsiniz:  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 WAS için olun bu hatayı görürseniz HTTP olmayan etkinleştirme yüklenmeli ve düzgün şekilde yapılandırılmalıdır. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: WCF etkinleştirme bileşenlerini yükleyip](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Bir WCF Hizmeti o kullanır, HTTP olmayan etkinleştirme için oluşturma  
 Yükleme ve WAS yapılandırma adımlarını gerçekleştirdikten sonra (bkz [nasıl yapılır: yükleme ve yapılandırma WCF etkinleştirme bileşenlerini](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), bir hizmetin WAS etkinleştirme IIS'de barındırılan bir hizmet yapılandırmaya benzer için yapılandırma.  
  
 WAS etkinleştirilmiş oluşturma hakkında ayrıntılı yönergeler için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet için bkz: [nasıl yapılır: bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows İşlem Etkinleştirme Hizmetinde Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
