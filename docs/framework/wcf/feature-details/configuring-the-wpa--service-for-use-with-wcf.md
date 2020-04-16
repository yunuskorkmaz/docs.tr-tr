---
title: Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 86e50b80d84479ca32b3d4d1fe3f205983640c76
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464163"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma
Bu konu, WINDOWS İletişim Vakfı (WCF) hizmetlerini barındırmak için Windows Vista'da Windows İşlem Etkinleştirme Hizmeti 'ni (WAS olarak da bilinir) ayarlamak için gereken adımları açıklar. Aşağıdaki bölümlerde bu yapılandırma için adımlar sıralar:  
  
- WCF etkinleştirme bileşenlerinin yüklenmesini (veya yüklenmesini onaylayın) gerekli.  
  
- Kullanmak istediğiniz ağ protokolü bağlayıcıları içeren bir WAS sitesi oluşturun veya varolan bir siteye yeni bir protokol bağlayıcısı ekleyin.  
  
- Hizmetlerinizi barındıracak ve bu uygulamanın gerekli ağ protokollerini kullanmasını sağlamak için bir uygulama oluşturun.  
  
- HTTP olmayan bir bitiş noktasını ortaya çıkaran bir WCF hizmeti oluşturun.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Bir Siteyi HTTP olmayan bağlamalarla yapılandırma  
 WAS ile non-HTTP bağlama kullanmak için, site bağlama WAS yapılandırmasına eklenmelidir. WAS için yapılandırma deposu %windir%\system32\inetsrv\config dizininde bulunan applicationHost.config dosyasıdır. Bu yapılandırma deposu hem WAS hem de IIS 7.0 tarafından paylaşılır.  
  
 applicationHost.config herhangi bir standart metin düzenleyicisi (Not Defteri gibi) ile açılabilir bir XML metin dosyasıdır. Ancak, IIS 7.0 komut satırı yapılandırma aracı (appcmd.exe) non-HTTP site bağlamaları eklemek için tercih edilen yoldur.  
  
 Aşağıdaki komut appcmd.exe kullanarak varsayılan Web sitesine bir net.tcp sitesi bağlama ekler (bu komut tek bir satır olarak girilir).  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Bu komut, applicationHost.config dosyasına aşağıda belirtilen satırı ekleyerek varsayılan Web sitesine yeni net.tcp bağlama ekler.  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Bir Uygulamanın HTTP Dışı Protokolleri Kullanmasını Etkinleştirme  
 Tek tek ağ protokollerini uygulama düzeyinde etkinleştirebilir veya devre dışı kullanabilirsiniz. Aşağıdaki komut, `Default Web Site`'de çalışan bir uygulama için HEM HTTP hem de net.tcp protokollerinin nasıl etkinleştirilen gösteriş olduğunu göstermektedir.  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Etkin protokollerin listesi applicationDefaults> \<sitenin XML yapılandırmasının ApplicationHost.config depolanan öğesi ayarlanabilir.  
  
 ApplicationHost.config aşağıdaki XML kodu hem HTTP ve non-HTTP protokolleri bağlı bir site göstermektedir. HTTP olmayan protokolleri desteklemek için gereken ek yapılandırma açıklamalarla birlikte çağrılır.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
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
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 Bir hizmeti HTTP dışı etkinleştirme için WAS'ı kullanarak etkinleştirmeye çalışırsanız ve WAS'ı yüklemediyseniz ve yapılandırmadıysanız aşağıdaki hatayı görebilirsiniz:  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Bu hatayı görürseniz, HTTP'siz Etkinleştirme için WAS'ın düzgün şekilde yüklendiğinden ve yapılandırıldığından emin olun. Daha fazla bilgi için [bkz: WCF Etkinleştirme Bileşenlerini Yükleyin ve Yapılandırın.](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>HTTP dışı etkinleştirme için WAS kullanan bir WCF Hizmeti Oluşturma  
 WAS'ı yüklemek ve yapılandırmak için adımları gerçekleştirdiğinizde [(bkz. WCF Etkinleştirme Bileşenlerini Nasıl Yükleyin ve Yapılandırın),](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)etkinleştirme için WAS'ı kullanacak bir hizmeti yapılandırmak, IIS'de barındırılan bir hizmeti yapılandırmaya benzer.  
  
 WAS tarafından etkinleştirilen bir WCF hizmeti oluşturma yla ilgili ayrıntılı talimatlar için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows İşlem Etkinleştirme Hizmetinde Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- [Windows Server App Kumaş Barındırma Özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
