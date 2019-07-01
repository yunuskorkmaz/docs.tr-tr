---
title: Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 7ab62bda5e579bcd80a7403d9af3a7e7f9836647
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486998"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma
Bu konu, Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) ' için gerekli adımları açıklar. [!INCLUDE[wv](../../../../includes/wv-md.md)] Windows Communication Foundation (WCF) barındırmak için HTTP üzerinden iletişim kurmazlar Hizmetleri protokolleri ağ. Aşağıdaki bölümlerde, bu yapılandırmanın adımları özetlemektedir:  
  
- Yükleme (veya yüklenmesini onaylayın) gerekli WCF etkinleştirme bileşenlerini.  
  
- Kullanmak istediğiniz ağ protokolü bağlamaları ile WAS site oluşturma veya mevcut bir site için yeni bir protokol bağlama ekleyin.  
  
- Hizmetlerinizi barındırmak ve bu uygulamayı gerekli ağ protokolleri kullanmak üzere etkinleştirmek için bir uygulama oluşturun.  
  
- HTTP olmayan uç noktasını kullanıma sunar bir WCF Hizmeti oluşturun.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Bir Site ile HTTP olmayan bağlamaları yapılandırma  
 Bir HTTP olmayan bağlama WAS ile kullanmak için bir site bağlaması için WAS yapılandırma eklenmesi gerekir. WAS yapılandırma mağazada %windir%\system32\inetsrv\config dizininde bulunan applicationHost.config dosyasıdır. Bu yapılandırma deposu WAS ve IIS 7.0 tarafından paylaşılır.  
  
 applicationHost.config standart bir metin düzenleyicisinde (Not Defteri gibi) ile açılmış bir XML metin dosyasıdır. Bununla birlikte, IIS 7.0 yapılandırma komut satırı aracı (appcmd.exe) HTTP olmayan site bağlamaları eklemek için tercih edilen yoludur.  
  
 Aşağıdaki komutu (Bu komut, tek bir satır olarak girilir) appcmd.exe kullanarak varsayılan Web sitesi net.tcp site bağlaması ekler.  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Bu komut, yeni net.tcp bağlama applicationHost.config dosyasına aşağıda belirtilen satır ekleyerek varsayılan Web sitesine ekler.  
  
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
 Etkinleştirmek veya tek tek ağ protocolsat uygulama düzeyinde devre dışı bırakabilirsiniz. Aşağıdaki komutu çalışan bir uygulama için hem HTTP hem de net.tcp protokolleri etkinleştirme gösterir `Default Web Site`.  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Etkin protokoller listesinde de ayarlanabilir \<applicationDefaults > ApplicationHost.config dosyasında depolanan sitenin XML yapılandırma öğesi.  
  
 Aşağıdaki XML kodunu applicationHost.config'den hem HTTP hem de HTTP olmayan protokolleri için ilişkili bir site gösterilmektedir. HTTP olmayan protokolleri desteklemek için gereken ek yapılandırma yorumlarla çağırılır.  
  
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
  
 HTTP olmayan etkinleştirme için WAS'ı kullanarak hizmeti etkinleştirin dener ve yüklenmediğinde veya WAS yapılandırılmış şu hatayı görebilirsiniz:  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 WAS için emin olun. Bu hatayı görürseniz, HTTP olmayan etkinleştirme yüklü ve düzgün yapılandırılmış. Daha fazla bilgi için [nasıl yapılır: WCF etkinleştirme bileşenlerini yükleme ve yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Bir WCF hizmeti, kullanan olan HTTP olmayan etkinleştirme için oluşturma  
 Yükleme ve WAS'ta yapılandırma adımlarını gerçekleştirdikten sonra (bkz [nasıl yapılır: Yükleme ve yapılandırma WCF etkinleştirme bileşenlerini](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), bir hizmetin WAS etkinleştirme IIS'de barındırılan bir hizmet yapılandırmaya benzer için yapılandırma.  
  
 WAS etkinleştirilmiş WCF hizmeti oluşturma hakkında ayrıntılı yönergeler için bkz: [nasıl yapılır: Was'ta WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows İşlem Etkinleştirme Hizmetinde Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
