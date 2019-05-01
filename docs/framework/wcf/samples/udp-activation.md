---
title: UDP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 6e19e92872c9b9344db7e787f0cd77e0a315f1a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007675"
---
# <a name="udp-activation"></a>UDP Etkinleştirme
Bu örnek dayanır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek. Bunu genişleten [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Windows İşlem Etkinleştirme Hizmeti (WAS) kullanarak işlem etkinleştirmeyi desteklemek için örnek.  
  
 Örnek üç ana parçalarını oluşur:  
  
- Bir UDP protokolünü Etkinleştirici, etkinleştirilecek olan uygulamaları adına UDP iletiler alan bir tek başına işlemi.  
  
- İleti göndermek için özel UDP taşıma kullanan bir istemci.  
  
- UDP özel taşıma iletileri alır (WAS tarafından etkinleştirilen bir çalışan işleminin içinde barındırılan) bir hizmettir.  
  
## <a name="udp-protocol-activator"></a>UDP protokolünü etkinleştiricisi  
 UDP protokolünü Etkinleştirici WCF istemcisini ve WCF hizmeti arasında bir köprü ' dir. Bu aktarım katmanında UDP protokolünü aracılığıyla veri iletişimi sağlar. İki ana işlev içerir:  
  
- Dinleyici Bağdaştırıcısı (gelen iletilere yanıt olarak işlemleri etkinleştirmeyi WAS ile iş Birliği yapar, LA), oldu.  
  
- UDP protokolünü UDP iletileri etkinleştirilecek olan uygulamaları adına kabul eden dinleyici.  
  
 Etkinleştirici sunucunuz üzerinde bağımsız bir program olarak çalıştırılması gerekir. Normalde, WAS dinleyici bağdaştırıcıları (örneğin, NetTcpActivator ve NetPipeActivator) uzun süre çalışan Windows Hizmetleri uygulanır. Ancak, Basitlik ve Anlaşılırlık için bu örnek, Protokolü Etkinleştirici tek başına uygulama'e uygular.  
  
### <a name="was-listener-adapter"></a>Dinleyici Bağdaştırıcısı OLUŞTU  
 UDP için olan dinleyici bağdaştırıcısı uygulanan `UdpListenerAdapter` sınıfı. WAS uygulama etkinleştirme için UDP protokolünü gerçekleştirmek için etkileşimde modüldür. Bu, aşağıdaki Web barındırma API'ları çağırarak sağlanır:  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 Başlangıçta çağrıldıktan sonra `WebhostRegisterProtocol`, dinleyici bağdaştırıcısı geri çağırma alır `ApplicationCreated` WAS tüm uygulamalar için gelen applicationHost.config (windir%\system32\inetsrv içinde bulunur) kaydedildi. Bu örnekte biz yalnızca etkin uygulamalarla UDP protokolünü ("net.udp" olarak Protokolü kimliği ile) işleyin. Diğer uygulamalar gibi uygulamaları (örneğin, bir uygulamanın durumundan etkin, devre dışı) uygulamaya dinamik yapılandırma değişikliklerine yanıt verme durumunda bu farklı şekilde işleyebilir.  
  
 Zaman geri çağırma `ConfigManagerInitializationCompleted` alınan, gösterir, WAS tüm başlatma protokolü için bildirim bitirdi. Şu anda Dinleyici Bağdaştırıcısı etkinleştirme isteklerini işlemek hazırdır.  
  
 Bir uygulama için ilk saatteki yeni bir istek geldiğinde, dinleyici bağdaştırıcısı çağırır `WebhostOpenListenerChannelInstance` WAS içinde çalışan işlemi henüz başlatılmamışsa başlatan. Ardından protokol işleyiciler yüklenir ve Dinleyici Bağdaştırıcısı ile sanal uygulama arasındaki iletişimi başlayabilir.  
  
 Dinleyici Bağdaştırıcısı içinde %SystemRoot%\System32\inetsrv\ApplicationHost.config kaydedilmiştir <`listenerAdapters`> bölümünde aşağıdaki gibi:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Dinleyici Protokolü  
 UDP protokolünü dinleyicisi UDP uç noktada dinleyen adına sanal uygulama protokolü Etkinleştirici içinde bir modüldür. Bu sınıfta uygulandığını `UdpSocketListener`. Uç nokta olarak temsil edilen `IPEndpoint` Protokolü site için bağlamayı, bağlantı noktası numarasını ayıklanan için.  
  
### <a name="control-service"></a>Hizmet denetimi  
 Bu örnekte, WCF Etkinleştirici ve WAS alt işlem arasında iletişim kurmak için kullanırız. Etkinleştirici içinde bulunan hizmet denetim hizmeti olarak adlandırılır.  
  
## <a name="protocol-handlers"></a>Protokol işleyiciler  
 Dinleyici Bağdaştırıcısı çağırdıktan sonra `WebhostOpenListenerChannelInstance`, onu başlatılmadığında WAS İşlem Yöneticisi'ni çalışan işlemi başlatır. Çalışan işlemi içinde uygulama Yöneticisi daha sonra UDP işlem protokol işleyicisi (PPH) söz konusu istekle yükler `ListenerChannelId`. Sırayla çağrılarındaki PPH `IAdphManager`.`StartAppDomainProtocolListenerChannel` UDP AppDomain protokol işleyicisi (ADPH) başlatmak için.  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Bilgiler, Web.config dosyasında şu şekilde kaydedilir:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Bu örnek için özel kurulum  
 Bu örnek yalnızca oluşturulan ve Windows Vista, Windows Server 2008 veya Windows 7 üzerinde çalıştırın. Örneği çalıştırmak için önce tüm bileşenlerin doğru bir şekilde ayarlandığından almanız gerekir. Örneği yüklemek için aşağıdaki adımları kullanın.  
  
#### <a name="to-set-up-this-sample"></a>Bu örneğini kurmak için  
  
1. Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Windows Vista'da projeyi derleyin. Derlemeden sonra ayrıca derleme sonrası aşamasında aşağıdaki işlemleri gerçekleştirir:  
  
    - UDP bağlama "varsayılan Web sitesi" alanına yükler.  
  
    - Fiziksel yolu işaret edecek şekilde sanal uygulama "ServiceModelSamples" oluşturur: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    - Ayrıca, bu sanal uygulama için "net.udp" protokol sağlar.  
  
3. "WasNetActivator.exe" kullanıcı arabirimi uygulamasını başlatın. Tıklayın **Kurulum** sekmesinde, aşağıdaki onay kutularını işaretleyin ve ardından **yükleme** bunları yüklemek için:  
  
    - UDP Dinleyici Bağdaştırıcısı  
  
    - UDP protokol işleyiciler  
  
4. Tıklayın **etkinleştirme** sekmesinde kullanıcı arabirimi uygulamasını "WasNetActivator.exe". Tıklayın **Başlat** dinleyici bağdaştırıcısını başlatma düğmesi. Programı çalıştırmak hazırsınız.  
  
    > [!NOTE]
    >  Bu örnek ile işiniz bittiğinde, "varsayılan Web sitesinden" net.udp bağlamayı kaldırmak Cleanup.bat çalıştırmanız gerekir.  
  
## <a name="sample-usage"></a>Örnek kullanımı  
 Derleme oluşturulan dört farklı ikili dosyaları vardır:  
  
- Client.exe: İstemci kodu. App.config Client.exe.config istemci yapılandırma dosyasına derlenir.  
  
- UDPActivation.dll: tüm önemli UDP uygulamaları içeren kitaplık.  
  
- Service.dll: Hizmet kodu. Bu sanal uygulama ServiceModelSamples \bin dizinine kopyalanır. Web.config yapılandırma dosyasıdır ve Service.svc hizmet dosyasıdır. Derleme şu konuma kopyalanır: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
- WasNetActivator: UDP Etkinleştirici program.  
  
- Tüm gerekli parçaları düzgün yüklendiğinden emin olun. Aşağıdaki adımlarda, örnek çalıştırmak gösterilmektedir:  
  
1. Aşağıdaki Windows Hizmetleri başlatıldığından emin olun:  
  
    - Windows İşlem Etkinleştirme Hizmeti (WAS).  
  
    - Internet Information Services (IIS): W3SVC.  
  
2. Daha sonra WasNetActivator.exe Etkinleştirici başlatın. Altında **etkinleştirme** sekmesi, tek protokol **UDP**, aşağı açılan listeden seçilir. Tıklayın **Başlat** düğmesi Etkinleştirici başlatılamadı.  
  
3. Etkinleştirici başlatıldıktan sonra bir komut penceresinden Client.exe çalıştırarak, istemci kodu çalıştırabilirsiniz. Örnek çıktı verilmiştir:  
  
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
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
