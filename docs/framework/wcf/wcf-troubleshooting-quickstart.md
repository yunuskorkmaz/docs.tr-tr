---
title: "WCF Sorun Giderme Hızlı Başlangıç"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d464042411b2d06368bb596e6d8d1dc0976808e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-troubleshooting-quickstart"></a>WCF Sorun Giderme Hızlı Başlangıç
Bu konuda müşteriler içine geliştirme WCF istemcileri ve Hizmetleri sırasında çalıştırdığınız bilinen sorunlar sayısını listeler. İçine çalıştırdığınız sorunu bu listede değilse, hizmetiniz için izleme yapılandırma öneririz. Bu bir izleme dosyası oluşturur izleme dosyası Görüntüleyici ile birlikte görüntülemek ve özel durumlar hakkında ayrıntılı bilgi almak hizmet içinde gerçekleşen. İzlemeyi yapılandırma hakkında daha fazla bilgi için bkz: [yapılandırma izleme](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). İzleme dosyası Görüntüleyici hakkında daha fazla bilgi için bkz: [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1.  [Bir WCF hizmetine göz atmak çalıştığınızda Windows 7 ve IIS yükledikten sonra aşağıdaki hata iletisi alıyorum: HTTP Hata 404.3 – bulunamadı](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     HTTP Hatası 404.3 – değil isteyen FoundThe sayfa uzantı yapılandırması nedeniyle sunulamıyor. Sayfa bir komut dosyası ise, bir işleyici ekleyin. Dosyanın indirilmesi gerekiyorsa, bir MIME eşlemesi ekleyin. Ayrıntılı hata InformationModule StaticFileModule.  
  
2.  [My istemci bir süre sonra ilk istek için boşta kalırsa bazen MessageSecurityException ikinci isteğinde alıyorum. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [Yaklaşık 10 istemcileri ile etkileşim sonra yeni istemciler reddetmeye My hizmetini başlatır. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [Hizmet yapılandırma sıralandığından WCF uygulamanın yapılandırma dosyasında diğer gelen yükleyebilir?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [Hizmetim ve istemci iş mükemmel, ancak bunları istemci başka bir bilgisayarda olduğunda iş alınamıyor? Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [Bir FaultException ı throw zaman\<özel durum > türü özel bir durum olduğunda, her zaman istemci üzerinde genel bir FaultException tür ve genel tür alıyorum. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [Gibi tek yönlü görünür ve yanıt hiçbir veri içerdiğinde istek-yanıt işlemleri kabaca aynı hızda döndürür. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [Bir X.509 sertifikası ile Hizmetim kullanıyorum ve bir System.Security.Cryptography.CryptographicException alın. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [Bir işlemin ilk parametre gelen büyük değiştirdim küçük harf için; Şimdi my istemcisi bir özel durum oluşturur. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [My izleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException alın. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [WCF Web HTTP uygulama hizmeti bir WCF SOAP uygulamasından çağırma döndüğünde aşağıdaki hata: 405 yöntemini verilmiyor](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [Temel adres nedir? Bu bir uç nokta adresine nasıl ilişkilidir?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Bir WCF hizmetine göz atmak çalıştığınızda Windows 7 ve IIS yükledikten sonra aşağıdaki hata iletisi alıyorum: HTTP Hata 404.3 – bulunamadı  
 Tam hata iletisi şudur:  
  
 HTTP Hatası 404.3 – değil isteyen FoundThe sayfa uzantı yapılandırması nedeniyle sunulamıyor. Sayfa bir komut dosyası ise, bir işleyici ekleyin. Dosyanın indirilmesi gerekiyorsa, bir MIME eşlemesi ekleyin. Ayrıntılı hata InformationModule StaticFileModule.  
  
 Bu hata iletisi, "Windows Communication Foundation HTTP etkinleştirme" Denetim Masası'nda açıkça ayarlanmadı oluşur. Denetim Masası'na bu Git ayarlamak için pencerenin alt sol alt köşede Programlar'ı tıklatın. Windows özelliklerini açmak veya kapatmak'ı tıklatın. Microsoft .NET Framework 3.5.1 genişletin ve Windows Communication Foundation HTTP Etkinleştirmesi'ni seçin.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>My istemci bir süre sonra ilk istek için boşta kalırsa bazen MessageSecurityException ikinci isteğinde alıyorum. Ne oluyor?  
 İkinci bir istek temelde iki nedenden dolayı başarısız olabilir: (1 oturum zaman aşımına uğradı veya barındırma hizmeti (2 Web sunucusu dönüştürülmeden. İlk durumda hizmeti zaman aşımına uğrayana kadar oturum geçerli değil. Ne zaman hizmeti almaz bir istek istemciden hizmetin bağlamada belirtilen süre içinde (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), hizmet güvenlik oturumu sona erer. Sonraki istemci iletileri neden <xref:System.ServiceModel.Security.MessageSecurityException>. İstemci, gelecekteki iletileri göndermek veya bir durum bilgisi olan güvenlik bağlamı belirteci kullanmak için hizmet ile güvenli bir oturumu yeniden oluşturmanız gerekir. Durum bilgisi olan güvenlik bağlamı belirteçleri dönüştürüldüğü bir Web sunucusu varlığını sürdürmesi güvenli bir oturum de olanak sağlar. [!INCLUDE[crabout](../../../includes/crabout-md.md)]durum bilgisi olan güvenli içeriği belirteçleri kullanarak güvenli bir oturumda bkz [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Alternatif olarak, güvenli oturumlar devre dışı bırakabilirsiniz. Kullandığınızda [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ayarlayabileceğiniz bağlama, `establishSecurityContext` özelliğine `false` güvenli oturumlar devre dışı bırakmak için. Güvenli oturumlar diğer bağlantılar için devre dışı bırakmak için özel bağlama oluşturmanız gerekir. Özel bağlama oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: SecurityBindingElement kullanarak özel bir bağlama oluşturun](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Bu seçeneklerin hiçbirini uygulamadan önce uygulamanızın güvenlik gereksinimlerini anlamanız gerekir.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Yaklaşık 10 istemcileri ile etkileşim sonra yeni istemciler reddetmeye My hizmetini başlatır. Ne oluyor?  
 Varsayılan olarak, yalnızca 10 eşzamanlı oturum Hizmetleri olabilir. Hizmet bağlamaları oturumları kullanırsanız, daha sonra yeni istemci bağlantılarını bir geçerli oturum sona kadar reddediyor bu sayıyı ulaşana kadar bu nedenle, hizmetin yeni istemci bağlantılarını kabul eder. Daha fazla istemciyi çeşitli yollarla destekleyebilir. Hizmetinizi oturumları gerektirmiyorsa, bir süre sonuyla bağlama kullanmayın. ([!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Oturumları kullanarak](../../../docs/framework/wcf/using-sessions.md).) Değerini değiştirerek oturum sınırı artırmak için başka bir seçenektir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> özelliği, koşullar uygun sayısı.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Hizmet yapılandırma sıralandığından WCF uygulamanın yapılandırma dosyasında diğer gelen yükleyebilir?  
 Evet, ancak özel bir oluşturmak kullandığınız <xref:System.ServiceModel.ServiceHost> geçersiz kılmaları sınıf <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yöntemi. Bu yöntem içinde (Standart yapılandırma bilgilerini de yüklemek istiyorsanız) yapılandırma önce yüklemek için temel çağırabilir ancak sistemi yükleme yapılandırması da tamamen değiştirebilirsiniz. Uygulama yapılandırma dosyasında farklı bir yapılandırma dosyasından yapılandırma yüklemek istiyorsanız, gerekir kendiniz yapılandırma dosyası ayrıştırma ve yapılandırmayı unutmayın.  
  
 Aşağıdaki kod örneğinde nasıl geçersiz kılınacağını gösterir <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yöntemi ve doğrudan bir uç noktasını yapılandırın.  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)    
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>   
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Hizmetim ve istemci iş mükemmel, ancak bunları istemci başka bir bilgisayarda olduğunda iş alınamıyor? Ne oluyor?  
 Özel duruma bağlı olarak, çeşitli sorunları olabilir:  
  
-   Ana bilgisayar adı ve değil "localhost" istemci uç nokta adresleri değiştirmeniz gerekebilir.  
  
-   Uygulama bağlantı noktasını açmanız gerekebilir. Ayrıntılar için bkz [güvenlik duvarı yönergeleri](../../../docs/framework/wcf/samples/firewall-instructions.md) SDK örnekleri gelen.  
  
-   Diğer olası sorunları için örnekleri konusuna [bir çalışma grubu ve üzerinden makineler örneklerini çalıştırma](http://msdn.microsoft.com/en-us/a451a525-e7ce-452d-9da9-620221260113).  
  
-   İstemci Windows kimlik bilgilerini kullanarak ve özel durum bir <xref:System.ServiceModel.Security.SecurityNegotiationException>, Kerberos aşağıdaki gibi yapılandırın.  
  
    1.  Kimlik bilgilerinin istemcinin App.config dosyasında son nokta öğesine ekleyin:  
  
        ```xml
        <endpoint   
          address="http://MyServer:8000/MyService/"   
          binding="wsHttpBinding"   
          bindingConfiguration="WSHttpBinding_IServiceExample"   
          contract="IServiceExample"   
          behaviorConfiguration="ClientCredBehavior"   
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2.  Kendini barındıran hizmet Sistem veya ağ hizmeti hesabı altında çalıştırın. Bu komutu bir komut penceresi sistem hesabı altında oluşturmak için çalıştırabilirsiniz:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  Altında Internet Information Services (varsayılan olarak, hizmet asıl adı (SPN) hesabı kullanır, IIS), hizmetini barındırır.  
  
    4.  Yeni bir SPN SetSPN kullanarak etki alanı ile kaydedin. Bunu yapmak için bir etki alanı yöneticisi olması gerektiğine dikkat edin.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Kerberos protokolü Bkz [WCF güvenlik kavramları kullanılan](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) ve:  
  
-   [Windows kimlik doğrulama hatalarını ayıklama](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [Http.sys kullanarak Kerberos hizmet asıl adlarını kaydetme](http://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [Kerberos açıklanmıştır](http://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Bir FaultException ı throw zaman\<özel durum > türü özel bir durum olduğunda, her zaman istemci üzerinde genel bir FaultException tür ve genel tür alıyorum. Ne oluyor?  
 Veri türü ve, hatalı sözleşme ayrıntı türü olarak bildirme kendi özel hata oluşturmak önerilir. Neden olan sistem tarafından sağlanan özel durum türleri kullanma:  
  
-   Hizmet odaklı uygulamalar büyük gücü birini kaldırır türü bağımlılığı oluşturur.  
  
-   Özel durumlar standart bir şekilde seri hale getirme sırasında bağımlı olamaz. Bazı — gibi <xref:System.Security.SecurityException>— hiç seri hale getirilebilir olmayabilir.  
  
-   İstemcilere iç uygulama ayrıntılarını gösterir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Belirtme ve sözleşme ve hizmetlerde hataları işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Bir uygulamada hata ayıklama yaparsanız, ancak, özel durum bilgilerini serileştirme ve kullanarak istemciye Döndür <xref:System.ServiceModel.Description.ServiceDebugBehavior> sınıfı.  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Gibi tek yönlü görünür ve yanıt hiçbir veri içerdiğinde istek-yanıt işlemleri kabaca aynı hızda döndürür. Ne oluyor?  
 Bir işlem bir yolu olduğunu belirten yalnızca işlem sözleşmesi bir giriş iletisi kabul eder ve bir çıktı iletisi döndürmüyor anlamına gelir. İçinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], tüm istemci çağrılarını giden veri kablo için yazılmış veya bir özel durum döndürür. Tek yönlü işlemler aynı şekilde çalışır ve hizmet bulunması veya hizmet ağdan verileri kabul etmek için hazır değil bloke atabilirsiniz. Genellikle, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], bu istemci istek-yanıt; daha hızlı döndüren tek yönlü çağrıları sonuçlanır ancak istek-yanıt işlemlerinin yanı sıra tek yönlü işlemler giden verilerin ağ üzerinden gönderilmesi yavaşlatır herhangi bir koşul yavaşlatır. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Tek yönlü Hizmetler](../../../docs/framework/wcf/feature-details/one-way-services.md) ve [bir WCF istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Bir X.509 sertifikası ile Hizmetim kullanıyorum ve bir System.Security.Cryptography.CryptographicException alın. Ne oluyor?  
 Bu, genellikle IIS çalışan altında çalıştığı işlemi kullanıcı hesabı değiştirdikten sonra gerçekleşir. Örneğin, [!INCLUDE[wxp](../../../includes/wxp-md.md)], Aspnet_wp.exe ASPNET bir özel kullanıcı hesabına çalıştığı varsayılan kullanıcı hesabını değiştirirseniz, bu hatayı görebilirsiniz. Özel anahtarı kullanıyorsanız, bunu kullanan işleme anahtara depolandığı dosya erişim iznine sahip gerekecektir.  
  
 Bu durumda, özel anahtarı içeren dosyayı için işlemin hesaba okuma erişimi ayrıcalıkları vermeniz gerekir. Örneğin, IIS çalışan işlemi Bob hesabı altında çalışıyorsa, özel anahtarı içeren dosyanın Bob okuma erişimi verin gerekecektir.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]belirli bir X.509 Sertifika özel anahtarı içeren dosyayı doğru kullanıcı hesabı erişimi vermek için bkz [nasıl yapılır: olun X.509 sertifikalarını WCF için erişilebilir](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Bir işlemin ilk parametre gelen büyük değiştirdim küçük harf için; Şimdi my istemcisi bir özel durum oluşturur. Ne oluyor?  
 Parametre adları işlemi imzada değerini sözleşmenin parçası olan ve büyük küçük harfe duyarlıdır. Kullanım <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> özniteliği yerel parametre adını ve işlem istemci uygulamaları için açıklayan meta veriler arasında ayrım gerektiğinde.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>My izleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException alın. Ne oluyor?  
 Sistem tarafından sağlanan değil bir izleme aracı kullanıyorsanız [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] izleme mekanizması ve alırsınız bir <xref:System.ServiceModel.EndpointNotFoundException> belirten bir adres filtresi uyuşmazlığı oluştu, kullanmanız gereken <xref:System.ServiceModel.Description.ClientViaBehavior> izleme iletilerini yönlendirmek için sınıfı yardımcı programı ve bu ileti hizmet adresine yönlendirmek yardımcı programı. <xref:System.ServiceModel.Description.ClientViaBehavior> Sınıfı değiştirir `Via` ayrı olarak alıcıdan ultimate, sonraki ağ adresini belirtmek için adresleme üstbilgi belirtilen tarafından `To` adresleme üstbilgi. Bunu yaparken kurmak için kullanılan uç nokta adresi ancak değiştirmeyin `To` değeri.  
  
 Aşağıdaki kod örneğinde bir örnek istemci yapılandırma dosyası gösterir.  
  
```xml
<endpoint   
  address=http://localhost:8000/MyServer/  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"   
  contract="IMyContract"   
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>   
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Temel adres nedir? Bu bir uç nokta adresine nasıl ilişkilidir?  
 Temel adres için kök adresidir bir <xref:System.ServiceModel.ServiceHost> sınıfı. Varsayılan olarak eklerseniz, bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> konak yayımlar tüm uç noktaları HTTP temel adresi yanı sıra meta veri davranışı için sağlanan tüm göreli adresi alınır için Web Hizmetleri Açıklama Dili (WSDL), hizmet yapılandırması sınıfı artı "? wsdl". Hakkında bilginiz varsa [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ve IIS, taban adresi sanal dizin ile eşdeğer ise.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Hizmet uç noktası ve NetTcpBinding kullanarak mex uç arasında bir bağlantı noktası paylaşımı  
 Net.tcp://MyServer bir hizmet için taban adresi belirtirseniz: 8080/MyService ve şu uç noktalar ekleyebilirsiniz:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 Ve NetTcpBinding ayarlarından birini aşağıdaki yapılandırma parçacığında gösterildiği gibi değiştirin:  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 Aşağıdaki gibi bir hata görürsünüz: işlenmeyen özel durum: System.ServiceModel.addressalreadyınuseexception: olduğundan zaten bir dinleyici IP uç noktası 0.0.0.0:9000 için farklı bir bağlantı noktası ile tam bir URL belirterek bu hataya çalışabilir Aşağıdaki yapılandırma parçacığında gösterildiği gibi MEX uç noktası:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>WCF Web HTTP uygulama hizmeti bir WCF SOAP uygulamasından çağırma döndüğünde aşağıdaki hata: 405 yöntemini verilmiyor  
 WCF Web HTTP uygulama çağırma (kullanan bir hizmet <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior>) bir WCF hizmeti şu özel durum oluşturabilir: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: Uzak sunucu beklenmeyen bir yanıt döndürdü : (405) yöntemi değil izin verilir.' WCF giden yazdığından bu özel durum oluştu <xref:System.ServiceModel.OperationContext> gelen ile <xref:System.ServiceModel.OperationContext>. Bu sorunu çözmek için oluşturun bir <xref:System.ServiceModel.OperationContextScope> WCF Web HTTP hizmeti işlemi içinde. Örneğin:  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows kimlik doğrulama hatalarını ayıklama](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
