---
title: UDP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 13444ab1be440c8e1a5f945cd512afa33772ea57
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044634"
---
# <a name="udp-activation"></a>UDP Etkinleştirme
Bu örnek, [aktarıma dayalıdır: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneği. [Taşımayı genişletir: Windows](../../../../docs/framework/wcf/samples/transport-udp.md) işlem etkinleştirme hizmeti (was) kullanılarak işlem etkinleştirmesini destekleyen UDP örneği.  
  
 Örnek üç ana parçadan oluşur:  
  
- Etkinleştirilecek uygulamalar adına UDP iletileri alan tek başına bir işlem olan UDP protokol Etkinleştirici.  
  
- İleti göndermek için UDP özel aktarımını kullanan bir istemci.  
  
- UDP özel aktarımı üzerinden ileti alan bir hizmet (tarafından etkinleştirilen bir çalışan işleminde barındırılan).  
  
## <a name="udp-protocol-activator"></a>UDP protokol Etkinleştirici  
 UDP protokol Etkinleştirici, WCF istemcisi ile WCF hizmeti arasında bir köprüdir. Aktarım katmanında UDP protokolü aracılığıyla veri iletişimi sağlar. İki ana işleve sahiptir:  
  
- İle işbirliği yapılan dinleyici bağdaştırıcısı (LA), gelen iletilere yanıt olarak işlemlerin ETKINLEŞTIRILME süreciydi.  
  
- Etkinleştirilecek uygulamalar adına UDP iletileri kabul eden UDP Protokol dinleyicisi.  
  
 Etkinleştirici, sunucu makinesinde tek başına bir program olarak çalışıyor olmalıdır. Normal olarak, WAS (Nettcpetkinleştirici ve Netpipeetkinleştirici gibi), uzun süre çalışan Windows hizmetlerinde uygulanan dinleyici bağdaştırıcılarıdır. Ancak kolaylık sağlaması ve açıklık için bu örnek, bağımsız bir uygulama olarak protokol Etkinleştirici uygular.  
  
### <a name="was-listener-adapter"></a>WAS dinleyicisi bağdaştırıcısı  
 UDP için was dinleyicisi bağdaştırıcısı `UdpListenerAdapter` sınıfında uygulanır. Bu, ile etkileşim kuran modüldür. Bu, aşağıdaki Webhost API 'Leri çağırarak elde edilir:  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 İlk çağrıldıktan `WebhostRegisterProtocol`sonra, dinleyici bağdaştırıcısı ApplicationHost. config dosyasında `ApplicationCreated` kayıtlı tüm uygulamalar için was geri çağırma işlemini alır (%Windir%\System32\inetsrv dizininde bulunur). Bu örnekte, yalnızca UDP protokolüne sahip uygulamaları (Protokol Kimliği "net. UDP") etkin olarak işleyeceğiz. Bu tür uygulamalar uygulamaya dinamik yapılandırma değişikliklerine yanıt vermezse (örneğin, devre dışı durumundan etkin 'e geçiş), diğer uygulamalar bunu farklı şekilde işleyebilir.  
  
 Geri arama `ConfigManagerInitializationCompleted` alındığında, bu, protokolünün başlatılmasına yönelik tüm bildirimlerin tamamlandığını gösterir. Şu anda, dinleyici bağdaştırıcısı etkinleştirme isteklerini işlemeye hazırlanıyor.  
  
 Bir uygulama için yeni bir istek ilk kez geldiğinde, dinleyici bağdaştırıcısı henüz başlatılmadıysa çalışan işlemini `WebhostOpenListenerChannelInstance` Başlatan was öğesine çağrılır. Ardından protokol işleyicileri yüklenir ve dinleyici bağdaştırıcısı ile sanal uygulama arasındaki iletişim başlatılabilir.  
  
 Dinleyici bağdaştırıcısı, aşağıdaki gibi <`listenerAdapters`> bölümünde%SystemRoot%\system32\ınetapplicationhost,config dizinine kaydedilir:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Protokol dinleyicisi  
 UDP Protokol dinleyicisi, sanal uygulama adına bir UDP uç noktasında dinleme yapan protokol Etkinleştirici içindeki bir modüldür. Sınıfında `UdpSocketListener`uygulanır. Uç noktası, bağlantı noktası `IPEndpoint` numarasının site için protokolün bağlamalarından ayıklandığı şekilde temsil edilir.  
  
### <a name="control-service"></a>Denetim Hizmeti  
 Bu örnekte, Etkinleştirici ile WAS çalışan işlemi arasında iletişim kurmak için WCF kullanırız. Etkinleştirici içinde bulunan hizmete denetim hizmeti denir.  
  
## <a name="protocol-handlers"></a>Protokol Işleyicileri  
 Dinleyici bağdaştırıcısı `WebhostOpenListenerChannelInstance`gerçekleştirildikten sonra, was işlem yöneticisi başlatılmamışsa çalışan işlemi başlatır. Ardından çalışan işleminin içindeki uygulama Yöneticisi, UDP Işlem Protokolü Işleyicisini (PPH) bunun isteğiyle `ListenerChannelId`yükler. İçindeki PPH, çağrıları `IAdphManager`dönüştürür.`StartAppDomainProtocolListenerChannel` UDP AppDomain protokol Işleyicisini (ADPH) başlatmak için.  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Bilgiler, Web. config dosyasına aşağıdaki şekilde kaydedilir:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Bu örnek için özel kurulum  
 Bu örnek yalnızca Windows Vista, Windows Server 2008 veya Windows 7 üzerinde oluşturulup çalıştırılabilir. Örneği çalıştırmak için, önce tüm bileşenlerin doğru şekilde ayarlanması gerekir. Örneği yüklemek için aşağıdaki adımları kullanın.  
  
#### <a name="to-set-up-this-sample"></a>Bu örneği ayarlamak için  
  
1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Projeyi Windows Vista 'da derleyin. Derlemeden sonra, derleme sonrası aşamasında aşağıdaki işlemleri de gerçekleştirir:  
  
    - "Default Web site" sitesine UDP bağlamasını kurar.  
  
    - "ServiceModelSamples" sanal uygulamasını "%SystemDrive%\inetpub\wwwroot\servicemodelsamples" fiziksel yolunu işaret etmek üzere oluşturur.  
  
    - Ayrıca, bu sanal uygulama için "net. UDP" protokolünü de sunar.  
  
3. "Tnewtactivator. exe" Kullanıcı arabirimi uygulamasını başlatın. **Kurulum** sekmesine tıklayın, aşağıdaki onay kutularını işaretleyin ve ardından yüklemek için **yükleme** ' ye tıklayın:  
  
    - UDP dinleyicisi bağdaştırıcısı  
  
    - UDP protokol Işleyicileri  
  
4. "Lınetactivator. exe" Kullanıcı arabirimi uygulamasının **etkinleştirme** sekmesine tıklayın. Dinleyici bağdaştırıcısını başlatmak için **Başlat** düğmesine tıklayın. Şimdi programı çalıştırmaya hazırsınız.  
  
    > [!NOTE]
    > Bu örnekle işiniz bittiğinde, "Default Web site" kaynağından net. UDP bağlamasını kaldırmak için Cleanup. bat dosyasını çalıştırmanız gerekir.  
  
## <a name="sample-usage"></a>Örnek kullanım  
 Derlemeden sonra oluşturulan dört farklı ikili dosya vardır:  
  
- Client. exe: İstemci kodu. App. config Client. exe. config istemci yapılandırma dosyasına derlenir.  
  
- UDPActivation. dll: tüm ana UDP uygulamalarını içeren kitaplık.  
  
- Service. dll: Hizmet kodu. Bu, ServiceModelSamples sanal uygulamasının \bin dizinine kopyalanır. Hizmet dosyası, Service. svc ve yapılandırma dosyası Web. config ' dir. Derlemeden sonra, bunlar şu konuma kopyalanır:%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
- , Ttactivator: UDP Etkinleştirici programı.  
  
- Tüm gerekli parçaların düzgün yüklendiğinden emin olun. Aşağıdaki adımlar, örneğin nasıl çalıştırılacağını göstermektedir:  
  
1. Aşağıdaki Windows hizmetlerinin başlatıldığından emin olun:  
  
    - Windows Işlem etkinleştirme hizmeti (WAS).  
  
    - Internet Information Services (IIS): ÇALIŞTIRIN.  
  
2. Ardından, etkinleştirentactivator. exe ' yi başlatın. **Etkinleştirme** sekmesi altında, iletişim kutusunda yalnızca **UDP**olan protokol seçilidir. Etkinleştirici 'yi başlatmak için **Başlat** düğmesine tıklayın.  
  
3. Etkinleştirici başlatıldıktan sonra, bir komut penceresinden Client. exe ' yi çalıştırarak istemci kodunu çalıştırabilirsiniz. Örnek çıktı aşağıda verilmiştir:  
  
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
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
