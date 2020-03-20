---
title: UDP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c0b351adb0b45f42404e94c74bdcff7785c2d0ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143726"
---
# <a name="udp-activation"></a>UDP Etkinleştirme
Bu örnek [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğine dayanmaktadır. Windows Process Etkinleştirme Hizmeti (WAS) kullanarak işlem etkinleştirme desteklemek için [Aktarım: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek genişletir.  
  
 Örnek üç ana parçadan oluşur:  
  
- Bir UDP Protokol Aktivatör, aktive edilecek uygulamalar adına UDP iletileri alan bağımsız bir işlemdir.  
  
- İleti göndermek için UDP özel aktarımını kullanan bir istemci.  
  
- UDP özel aktarım üzerinden ileti alan bir hizmet (WAS tarafından etkinleştirilen bir alt işlemde barındırılan).  
  
## <a name="udp-protocol-activator"></a>UDP Protokol Aktivatör  
 UDP Protokol Aktivatör WCF istemcisi ve WCF hizmeti arasında bir köprüdür. Aktarım katmanındaki UDP protokolü aracılığıyla veri iletişimi sağlar. İki ana işlevi vardır:  
  
- Gelen iletilere yanıt olarak süreçleri etkinleştirmek için WAS ile işbirliği yapan WAS Dinleyici Adaptörü (LA).  
  
- UdP Protokol Dinleyicisi, aktive edilecek uygulamalar adına UDP iletilerini kabul eder.  
  
 Etkinleştirme, sunucu makinesinde bağımsız bir program olarak çalışıyor olmalıdır. Normalde, WAS dinleyici adaptörleri (NetTcpActivator ve NetPipeActivator gibi) uzun süredir çalışan Windows hizmetlerinde uygulanır. Ancak, basitlik ve netlik için, bu örnek tek başına bir uygulama olarak protokol aktivatör uygular.  
  
### <a name="was-listener-adapter"></a>WAS Dinleyici Adaptörü  
 UDP için WAS Dinleyici Adaptörü `UdpListenerAdapter` sınıfta uygulanır. UDP protokolü için uygulama aktivasyonu gerçekleştirmek için WAS ile etkileşim modüldür. Bu, aşağıdaki Web host API'lerini arayarak elde edilir:  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 Başlangıçta aradıktan `WebhostRegisterProtocol`sonra, dinleyici adaptörü `ApplicationCreated` applicationHost.config kayıtlı tüm uygulamalar için WAS geri çağrı alır (% windir%\system32\inetsrv bulunur). Bu örnekte, uygulamaları yalnızca UDP protokolü (protokol kimliği "net.udp" olarak) etkinleştirilmiş olarak ele alıyoruz. Bu tür uygulamalar uygulamada dinamik yapılandırma değişikliklerine yanıt veriyorsa (örneğin, devre dışı bırakılan uygulamadan etkine bir uygulama geçişi) diğer uygulamalar bunu farklı şekilde işleyebilir.  
  
 Geri arama `ConfigManagerInitializationCompleted` yapıldığında, bt protokolün başlatılması için tüm bildirimleri tamamladığını gösterir. Şu anda, dinleyici bağdaştırıcı etkinleştirme isteklerini işlemeye hazırdır.  
  
 Bir uygulama için ilk kez yeni bir istek geldiğinde, `WebhostOpenListenerChannelInstance` dinleyici bağdaştırıcısı WAS'ı çağırır ve bu da henüz başlatılmazsa alt işlemi başlatır. Daha sonra protokol işleyicileri yüklenir ve dinleyici bağdaştırıcısı ile sanal uygulama arasındaki iletişim başlatılabilir.  
  
 Dinleyici bağdaştırıcısı <`listenerAdapters`> bölümünde %SystemRoot%\System32\Inetsrv\ApplicationHost.config'de aşağıdaki gibi kaydedilir:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Protokol Dinleyicisi  
 UDP protokol dinleyicisi, sanal uygulama adına UDP bitiş noktasında dinleyen protokol aktivatörünün içindeki bir modüldür. Bu sınıfta `UdpSocketListener`uygulanır. Bitiş noktası, bağlantı `IPEndpoint` noktası numarasının site için protokol ün bağlayıcılığından ayıklandığı şekilde temsil edilir.  
  
### <a name="control-service"></a>Kontrol Hizmeti  
 Bu örnekte, aktivatör ve WAS alt süreci arasında iletişim kurmak için WCF'yi kullanırız. Etkinleştirmede bulunan hizmete Denetim Hizmeti denir.  
  
## <a name="protocol-handlers"></a>Protokol Handleyicileri  
 Dinleyici bağdaştırıcısı çağrılarını `WebhostOpenListenerChannelInstance`yaptıktan sonra, başlatılmazsa WAS işlem yöneticisi alt işlemi başlatır. Alt işlem içindeki uygulama yöneticisi daha sonra udp işlem protokolü işleyicisi `ListenerChannelId`(PPH) için istek yükler. Sırayla PPH `IAdphManager`çağırır .`StartAppDomainProtocolListenerChannel` UDP AppDomain Protokol Handizor'yu (ADPH) başlatmak için.  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Bilgiler Web.config'de aşağıdaki gibi kaydedilir:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Bu Örnek için Özel Kurulum  
 Bu örnek yalnızca Windows Vista, Windows Server 2008 veya Windows 7'de oluşturulabilir ve çalıştırılabilir. Örneği çalıştırmak için öncelikle tüm bileşenleri doğru şekilde ayarlamanız gerekir. Örneği yüklemek için aşağıdaki adımları kullanın.  
  
#### <a name="to-set-up-this-sample"></a>Bu örneği ayarlamak için  
  
1. Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Projeyi Windows Vista'da oluşturun. Derlemeden sonra, yapı sonrası aşamada da aşağıdaki işlemleri gerçekleştirir:  
  
    - "Varsayılan Web Sitesi" sitesine bağlanan UDP'yi yükler.  
  
    - Fiziksel yolu işaret etmek için sanal uygulama "ServiceModelSamples" oluşturur: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    - Ayrıca bu sanal uygulama için "net.udp" protokolü sağlar.  
  
3. Kullanıcı arabirimi uygulamasını "WasNetActivator.exe" başlatın. **Kurulum** sekmesini tıklatın, aşağıdaki onay kutularını işaretleyin ve sonra yüklemek için **Yükle'yi** tıklatın:  
  
    - UDP Dinleyici Adaptörü  
  
    - UDP Protokol Handleyicileri  
  
4. Kullanıcı arabirimi uygulaması "WasNetActivator.exe" **etkinleştirme** sekmesini tıklatın. Dinleyici bağdaştırıcısını başlatmak için **Başlat** düğmesini tıklatın. Şimdi programı çalıştırmak için hazırsınız.  
  
    > [!NOTE]
    > Bu örnekle bitirdiğinizde, "Varsayılan Web Sitesi"nden net.udp bağlamayı kaldırmak için Cleanup.bat'ı çalıştırmanız gerekir.  
  
## <a name="sample-usage"></a>Örnek Kullanım  
 Derlemeden sonra oluşturulan dört farklı ikili vardır:  
  
- Client.exe: İstemci kodu. App.config istemci yapılandırma dosyasıclient.exe.config derlenir.  
  
- UDPActivation.dll: tüm önemli UDP uygulamalarını içeren kitaplık.  
  
- Service.dll: Servis kodu. Bu sanal uygulama ServiceModelSamples \bin dizinine kopyalanır. Hizmet dosyası Service.svc ve yapılandırma dosyası Web.config olduğunu. Derlemeden sonra aşağıdaki konuma kopyalanırlar: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
- WasNetActivator: UDP aktivatör programı.  
  
- Gerekli tüm parçaların doğru şekilde takıldığından emin olun. Aşağıdaki adımlar, örneğin nasıl çalıştırılsüreceğini gösterir:  
  
1. Aşağıdaki Windows hizmetlerinin başlatıldığından emin olun:  
  
    - Windows İşlem etkinleştirme Hizmeti (WAS).  
  
    - İnternet Bilgi Hizmetleri (IIS): W3SVC.  
  
2. Sonra aktivatör, WasNetActivator.exe başlatın. **Etkinleştirme** sekmesialtında, tek protokol, **UDP**, açılır listede seçilir. Etkinleştirme başlatmak için **Başlat** düğmesini tıklatın.  
  
3. Etkinleştirme başlatıldıktan sonra, istemci kodunu bir komut penceresinden Client.exe çalıştırarak çalıştırabilirsiniz. Örnek çıktı aşağıdaki gibidir:  
  
    ```console  
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
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
