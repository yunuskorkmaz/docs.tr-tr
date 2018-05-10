---
title: UDP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 9f7600bff17c015f28c3fb94ed5360561d45c65b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="udp-activation"></a>UDP Etkinleştirme
Bu örnek dayanır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek. Bunu genişletir [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Windows İşlem Etkinleştirme Hizmeti (WAS) kullanarak işlem etkinleştirmeyi desteklemek için örnek.  
  
 Örnek üç önemli parçaları oluşur:  
  
-   Bir UDP protokolünü Etkinleştirici, etkinleştirilmesi için olan uygulamaları adına UDP iletileri alan bir tek başına işlemi.  
  
-   İleti göndermek için UDP özel taşıma kullanan istemci.  
  
-   UDP özel taşıma iletileri alan (WAS tarafından etkinleştirilen bir çalışan işlemde barındırılan) bir hizmet.  
  
## <a name="udp-protocol-activator"></a>UDP protokolünü Etkinleştirici  
 UDP protokolünü Etkinleştirici WCF istemcisini ve WCF hizmeti arasında bir köprü ' dir. Aktarım katmanında UDP protokolü aracılığıyla veri iletişimi sağlar. İki ana işlevi vardır:  
  
-   Dinleyici Bağdaştırıcısı (hangi işlemleri gelen iletilere yanıt olarak etkinleştirmek için WAS ile güvenliktir LA), OLUŞTU.  
  
-   UDP protokol UDP iletileri etkinleştirilmesi için olan uygulamaları adına kabul eden dinleyicisi.  
  
 Etkinleştirici bağımsız bir program olarak server makinesinde çalıştırması gerekir. Normalde, uzun süre çalışan Windows Hizmetleri (örneğin, NetTcpActivator ve NetPipeActivator) WAS dinleyici bağdaştırıcılarına uygulanır. Ancak, Basitlik ve daha anlaşılır olması için bu örnek, Protokolü Etkinleştirici bir tek başına uygulama olarak'e uygular.  
  
### <a name="was-listener-adapter"></a>Dinleyici Bağdaştırıcısı edildi  
 UDP için olan dinleyici bağdaştırıcısı uygulanan `UdpListenerAdapter` sınıfı. WAS uygulama etkinleştirme için UDP protokolünü gerçekleştirmek için etkileşimde modüldür. Bu, aşağıdaki Webhost API'ları çağırarak sağlanır:  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 Başlangıçta çağrıldıktan sonra `WebhostRegisterProtocol`, geri çağırma Dinleyici Bağdaştırıcısı alır `ApplicationCreated` WAS tüm uygulamalar için gelen kayıtlı (windir%\system32\inetsrv içinde bulunur) applicationHost.config içinde. Bu örnekte, biz yalnızca etkin uygulamaları UDP protokolünü (kimlikli Protokolü "net.udp" olarak) ile işler. Bu tür uygulamalar (örneğin, etkin devre dışı bir uygulama geçiş) uygulamaya dinamik yapılandırma değişikliklerine yanıt verme durumunda diğer uygulamalar bu farklı şekilde işleyebilir.  
  
 Zaman geri çağırma `ConfigManagerInitializationCompleted` alınan, belirtir, WAS protokol başlatma bildirimlerini tümünün bitirdi. Bu aşamada, etkinleştirme isteklerini işlemek Dinleyici Bağdaştırıcısı hazırdır.  
  
 Bir uygulamayı ilk kez içinde yeni bir istek geldiğinde, dinleyici bağdaştırıcısını çağırır `WebhostOpenListenerChannelInstance` WAS başladığı çalışan işlemi henüz başlamamışsa. Ardından protokol işleyici yüklenir ve sanal uygulama ile dinleyici bağdaştırıcısı arasındaki iletişimi başlayabilirsiniz.  
  
 Dinleyici Bağdaştırıcısı %SystemRoot%\System32\inetsrv\ApplicationHost.config kayıtlı <`listenerAdapters`> bölümünde aşağıdaki gibi:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Protokol dinleyicisi  
 UDP protokolünü dinleyicisi UDP uç noktada sanal uygulama adına dinler Protokolü Etkinleştirici içinde bir modüldür. Sınıfında uygulanır `UdpSocketListener`. Uç nokta olarak temsil edilir `IPEndpoint` Protokolü bağlama site için hangi bağlantı noktası numarasını ayıklanan için.  
  
### <a name="control-service"></a>Denetim Hizmeti  
 Bu örnekte, WCF Etkinleştirici ve WAS çalışan işlem arasında iletişim kurmak için kullanırız. Etkinleştirici bulunduğu hizmet denetimi hizmeti adı verilir.  
  
## <a name="protocol-handlers"></a>Protokol işleyici  
 Dinleyici Bağdaştırıcısı çağrıları sonra `WebhostOpenListenerChannelInstance`, onu başlatılmadıysa WAS İşlem Yöneticisi'ni çalışan işlemi başlatır. Çalışan işlemi içinde uygulama Yöneticisi daha sonra UDP işlem protokol işleyici (PPH) söz konusu bir istekle yükler `ListenerChannelId`. Kapatır çağrılarında PPH `IAdphManager`.`StartAppDomainProtocolListenerChannel` UDP AppDomain protokol işleyici (ADPH) başlatmak için.  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Bilgiler Web.Config'de şu şekilde kaydedilir:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Bu örnek için özel kurulum  
 Bu örnek yalnızca yerleşik ve Windows Vista, Windows Server 2008 veya Windows 7'yi çalıştırın. Örneği çalıştırmak için önce doğru olarak ayarlanmış tüm bileşenleri edinmeniz gerekir. Örneği yüklemek için aşağıdaki adımları kullanın.  
  
#### <a name="to-set-up-this-sample"></a>Bu örneğini kurmak için  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Windows Vista'da projeyi oluşturun. Derleme sonra ayrıca oluşturma sonrası aşamasında aşağıdaki işlemleri gerçekleştirir:  
  
    -   UDP bağlama "Default Web Site" sitesine yükler.  
  
    -   Fiziksel yolu işaret edecek şekilde sanal uygulama "ServiceModelSamples" oluşturur: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    -   Ayrıca, bu sanal uygulama için "net.udp" Protokolü sağlar.  
  
3.  Kullanıcı arabirimini uygulaması "WasNetActivator.exe" başlatın. Tıklatın **Kurulum** sekmesinde, aşağıdaki onay kutularını işaretleyin ve ardından **yükleme** bunları yüklemek için:  
  
    -   UDP Dinleyici Bağdaştırıcısı  
  
    -   UDP protokol işleyici  
  
4.  Tıklatın **etkinleştirme** kullanıcı arabirimini uygulaması "WasNetActivator.exe" sekmesinde. Tıklatın **Başlat** Dinleyici Bağdaştırıcısı başlamak için Başlat. Şimdi program çalıştırılmaya hazır.  
  
    > [!NOTE]
    >  Bu örnek ile işiniz bittiğinde, gelen "Default Web Site" net.udp bağlama kaldırmak için Cleanup.bat çalıştırmanız gerekir.  
  
## <a name="sample-usage"></a>Örnek Kullanım  
 Derleme sonra oluşturulan dört farklı ikili dosyalar vardır:  
  
-   Client.exe: İstemci kodu. App.config istemci yapılandırma dosyasına Client.exe.config derlenir.  
  
-   UDPActivation.dll: tüm önemli UDP uygulamaları içeren kitaplığı.  
  
-   Service.dll: Hizmet kodu. Bu sanal uygulama ServiceModelSamples \bin dizinine kopyalanır. Hizmet dosyası Service.svc ve Web.config yapılandırma dosyası değil. Derleme sonra aşağıdaki konuma kopyalanmadığı: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
-   WasNetActivator: UDP Etkinleştirici program.  
  
-   Tüm gerekli parça doğru şekilde yüklendiğinden emin olun. Aşağıdaki adımlar örneği çalıştırma gösterir:  
  
1.  Aşağıdaki Windows hizmetlerin başlatıldığından emin olun:  
  
    -   Windows İşlem Etkinleştirme Hizmeti (WAS).  
  
    -   Internet Information Services (IIS): W3SVC.  
  
2.  Daha sonra WasNetActivator.exe Etkinleştirici başlatın. Altında **etkinleştirme** sekmesi, yalnızca Protokolü **UDP**, aşağı açılan listeden seçilir. Tıklatın **Başlat** Etkinleştirici başlamak için Başlat.  
  
3.  Etkinleştirici başladıktan sonra bir komut penceresinde Client.exe çalıştırarak, istemci kodu çalıştırabilirsiniz. Örnek çıktı verilmiştir:  
  
    ```  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a>Ayrıca Bkz.
