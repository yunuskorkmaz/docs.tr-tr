---
title: WCF Sorun Giderme Hızlı Başlangıç
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: f85d37fde19767d7fd1e3002776b4816666cc7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183049"
---
# <a name="wcf-troubleshooting-quickstart"></a>WCF Sorun Giderme Hızlı Başlangıç
Bu konu, müşterilerin WCF istemcileri ve hizmetleri geliştirirken karşılaştıkları bilinen bir dizi sorunu listeler. Üzerinde durmaktadırsorun bu listede değilse, hizmetiniz için izleme yapılandırmanızı öneririz. Bu, izleme dosyası görüntüleyicisiyle görüntüleyebileceğiniz bir izleme dosyası oluşturur ve hizmet içinde oluşabilecek özel durumlar hakkında ayrıntılı bilgi alır. İzlemeyi yapılandırma hakkında daha fazla bilgi için bkz: [İzlemeyi yapılandırma.](./diagnostics/tracing/configuring-tracing.md) İzleme dosyası görüntüleyici hakkında daha fazla bilgi için bkz: [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1. [Windows 7 ve IIS'yi yükledikten sonra, bir WCF hizmetine göz atmaya çalışırken aşağıdaki hata iletisini alıyorum: HTTP Hatası 404.3 – Bulunamadı](#bkmk_0)  
  
     HTTP Hata 404.3 – Bulunamadı İstediğiniz sayfa uzantı yapılandırması nedeniyle servis edilemez. Sayfa bir komut dosyasıysa, bir işleyici ekleyin. Dosya indirilecekse, bir MIME eşlemi ekleyin. Detaylı Hata Bilgisi Modülü StaticFileModule.  
  
2. [Bazen müşterim ilk istekten sonra bir süre boşta ise ikinci istek üzerine bir MessageSecurityException alırsınız. Ne oluyor?](#BKMK_q1)  
  
3. [Hizmetim, yaklaşık 10 istemci yle etkileşime geçtikten sonra yeni istemcileri reddetmeye başlar. Ne oluyor?](#BKMK_q2)  
  
4. [Hizmet yapılandırmamı WCF uygulamasının yapılandırma dosyası dışında bir yerden yükleyebilir miyim?](#BKMK_q3)  
  
5. [Hizmetim ve istemcim harika çalışıyor, ancak istemci başka bir bilgisayarda yken onları çalıştıramıyorum? Ne oluyor?](#BKMK_q4)  
  
6. [Tür özel durum\<> bir Hata Özel Durum atandığımda, her zaman istemci değil, genel türü genel bir Hata Özel Durum türü alırsınız. Ne oluyor?](#BKMK_q5)  
  
7. [Yanıt hiçbir veri içerdiğinde, tek yönlü ve istek yanıtlama işlemleri kabaca aynı hızda geri dönüyor gibi görünüyor. Ne oluyor?](#BKMK_q6)  
  
8. [Hizmetimde X.509 sertifikası kullanıyorum ve System.Security.Cryptography.CryptographicException alıyorum. Ne oluyor?](#BKMK_q77)  
  
9. [Bir işlemin ilk parametresini büyük harften küçük harfe değiştirdim; Şimdi müvekkilim bir istisna atıyor. Ne oluyor?](#BKMK_q88)  
  
10. [Benim izleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException olsun. Ne oluyor?](#BKMK_q99)  
  
11. [WCF SOAP uygulamasından WCF Web HTTP uygulamasını ararken hizmet aşağıdaki hatayı döndürür: 405 Yöntem İzin Verilmez](#BK_MK99)  
  
 [Temel adres nedir? Bitiş noktası adresiyle ne ilgisi var?](#BKMK_q10)  
  
<a name="bkmk_0"></a>
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Windows 7 ve IIS'yi yükledikten sonra, bir WCF hizmetine göz atmaya çalışırken aşağıdaki hata iletisini alıyorum: HTTP Hatası 404.3 – Bulunamadı  
 Tam hata iletisi:  
  
 HTTP Hata 404.3 – Bulunamadı İstediğiniz sayfa uzantı yapılandırması nedeniyle servis edilemez. Sayfa bir komut dosyasıysa, bir işleyici ekleyin. Dosya indirilecekse, bir MIME eşlemi ekleyin. Detaylı Hata Bilgisi Modülü StaticFileModule.  
  
 Bu hata iletisi, "Windows Communication Foundation HTTP Etkinleştirme" Denetim Masası'nda açıkça ayarlanmadığında oluşur. Bunu Denetim Masası'na ayarlamak için pencerenin sol alt köşesindeki Programlar'ı tıklatın. Windows özelliklerini aç veya kapat'ı tıklatın. Microsoft .NET Framework 3.5.1'i genişletin ve Windows Communication Foundation HTTP Etkinleştirme'yi seçin.  
  
<a name="BKMK_q1"></a>
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Bazen müşterim ilk istekten sonra bir süre boşta ise ikinci istek üzerine bir MessageSecurityException alırsınız. Ne oluyor?  
 İkinci istek öncelikle iki nedenden dolayı başarısız olabilir: (1) oturum zamanlanmış veya (2) hizmeti barındıran Web sunucusu geri dönüştürülür. İlk durumda, oturum hizmet saatleri bitene kadar geçerlidir. Hizmet, hizmetin bağlayıcısında belirtilen süre içinde istemciden bir istek almadığı<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>nda ( ), hizmet güvenlik oturumunu sonlandırır. Sonraki istemci iletileri <xref:System.ServiceModel.Security.MessageSecurityException>. İstemci, gelecekteki iletileri göndermek veya durum salkınlı bir güvenlik bağlamı belirteci kullanmak için hizmetle güvenli bir oturum oluşturmalı. Durumsal güvenlik bağlam belirteçleri, güvenli bir oturumun geri dönüştürülen bir Web sunucusundan hayatta kalmasına da olanak sağlar. Güvenli bir oturumda durum bilgisine uygun güvenli bağlam belirteçleri kullanma hakkında daha fazla bilgi için [bkz.](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md) Alternatif olarak, güvenli oturumları devre dışı bırakabilirsiniz. wsHttpBinding>bağlamayı kullandığınızda, `establishSecurityContext` özelliği güvenli `false` oturumları devre dışı bırakacak şekilde ayarlayabilirsiniz. [ \<](../configure-apps/file-schema/wcf/wshttpbinding.md) Diğer bağlamalar için güvenli oturumları devre dışı bırakabilmek için özel bir bağlama oluşturmanız gerekir. Özel bir bağlama oluşturma yla ilgili ayrıntılar için [bkz: SecurityBindingElement'i kullanarak Özel Bağlama Oluşturma.](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) Bu seçeneklerden herhangi birini uygulamadan önce, uygulamanızın güvenlik gereksinimlerini anlamanız gerekir.  
  
<a name="BKMK_q2"></a>
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Hizmetim, yaklaşık 10 istemci yle etkileşime geçtikten sonra yeni istemcileri reddetmeye başlar. Ne oluyor?  
 Varsayılan olarak, hizmetlerin yalnızca 10 eşzamanlı oturumu olabilir. Bu nedenle, hizmet oturumları kullanırsa, hizmet bu sayıya ulaşana kadar yeni istemci bağlantılarını kabul eder ve ardından geçerli oturumlardan biri sona erene kadar yeni istemci bağlantılarını reddeder. Daha fazla istemciyi çeşitli yollarla destekleyebilirsiniz. Hizmetiniz oturum gerektirmiyorsa, oturumlu bir bağlama kullanmayın. (Daha fazla bilgi için [bkz.](using-sessions.md) Başka bir seçenek, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> özelliğin değerini durumunuza uygun sayıyla değiştirerek oturum sınırını artırmaktır.  
  
<a name="BKMK_q3"></a>
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Hizmet yapılandırmamı WCF uygulamasının yapılandırma dosyası dışında bir yerden yükleyebilir miyim?  
 Evet, ancak, <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yöntemi geçersiz kılan özel bir sınıf oluşturmanız gerekir. Bu yöntemin içinde, önce yapılandırmayı yüklemek için tabanı arayabilirsiniz (standart yapılandırma bilgilerini de yüklemek istiyorsanız) ancak yapılandırma yükleme sistemini tamamen değiştirebilirsiniz. Yapılandırmayı uygulama yapılandırma dosyasından farklı bir yapılandırma dosyasından yüklemek istiyorsanız, yapılandırma dosyasını kendiniz ayrıştırmalı ve yapılandırmayı yüklemeniz gerekir.  
  
 Aşağıdaki kod örneği, yöntemi nasıl <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> geçersiz kılınan ve bir bitiş noktasının doğrudan nasıl yapılandırılabildiğini gösterir.  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Hizmetim ve istemcim harika çalışıyor, ancak istemci başka bir bilgisayarda yken onları çalıştıramıyorum? Ne oluyor?  
 Özel duruma bağlı olarak, çeşitli sorunlar olabilir:  
  
- İstemci bitiş noktası adreslerini "localhost" değil, ana bilgisayar adı olarak değiştirmeniz gerekebilir.  
  
- Bağlantı noktasını uygulamaya açmanız gerekebilir. Ayrıntılar için, SDK örneklerinden [Güvenlik Duvarı Yönergeleri'ne](./samples/firewall-instructions.md) bakın.  
  
- Diğer olası sorunlar için, [Windows Communication Foundation Samples'ı çalıştıran](./samples/running-the-samples.md)örnekler konusuna bakın.  
  
- İstemciniz Windows kimlik bilgilerini kullanıyorsa ve özel durum kerberos'u <xref:System.ServiceModel.Security.SecurityNegotiationException>aşağıdaki gibi yapılandırın.  
  
    1. Kimlik bilgilerini istemcinin App.config dosyasındaki bitiş noktası öğesine ekleyin:  
  
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
  
    2. Sistem veya NetworkService hesabı altında kendi kendine barındırılan hizmeti çalıştırın. Sistem hesabının altında bir komut penceresi oluşturmak için bu komutu çalıştırabilirsiniz:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. Hizmeti, varsayılan olarak hizmet ana adı (SPN) hesabını kullanan Internet Information Services (IIS) altında barındırın.  
  
    4. SetSPN kullanarak etki alanına yeni bir SPN kaydedin. Bunu yapmak için bir etki alanı yöneticisi olmanız gerekir.  
  
 Kerberos protokolü hakkında daha fazla bilgi için [WCF'de Kullanılan Güvenlik Kavramları'na](./feature-details/security-concepts-used-in-wcf.md) bakın ve:  
  
- [Windows Kimlik Doğrulama Hatalarını Ayıklama](./feature-details/debugging-windows-authentication-errors.md)  
  
- [Http.sys kullanarak Kerberos Hizmet Müdür Adları Kayıt](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))  
  
- [Kerberos Açıklaması](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))  
  
<a name="BKMK_q5"></a>
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Tür özel durum\<> bir Hata Özel Durum atandığımda, her zaman istemci değil, genel türü genel bir Hata Özel Durum türü alırsınız. Ne oluyor?  
 Kendi özel hata veri türünü oluşturmanız ve hata sözleşmenizdeki ayrıntı türü olarak bunu beyan etmeniz önerilir. Bunun nedeni, sistem tarafından sağlanan özel durum türlerini kullanarak:  
  
- Hizmet yönelimli uygulamaların en büyük güçlü yanlarından birini kaldıran bir tür bağımlılık oluşturur.  
  
- Standart bir şekilde seri hale getirme özel durumlara bağlı olamaz. Bazı-gibi <xref:System.Security.SecurityException>—hiç serializable olmayabilir.  
  
- Dahili uygulama ayrıntılarını istemcilere karşı ortaya çıkarır. Daha fazla bilgi için [bkz.](specifying-and-handling-faults-in-contracts-and-services.md)  
  
 Ancak, bir uygulamayı hata ayıklıyorsanız, özel durum bilgilerini serihale getirebilir ve <xref:System.ServiceModel.Description.ServiceDebugBehavior> sınıfı kullanarak istemciye döndürebilirsiniz.  
  
<a name="BKMK_q6"></a>
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Yanıt hiçbir veri içerdiğinde, tek yönlü ve istek yanıtlama işlemleri kabaca aynı hızda geri dönüyor gibi görünüyor. Ne oluyor?  
 Bir işlemin tek bir yol olduğunu belirtmek, yalnızca işlem sözleşmesinin bir giriş iletisi kabul ettiği ve çıktı iletisi döndürmemesi anlamına gelir. WCF'de, giden veriler kabloya yazıldığında veya bir özel durum atıldığında tüm istemci çağrıları geri döner. Tek yönlü işlemler aynı şekilde çalışır ve hizmet inanın ağından verileri kabul etmeye hazır değilse, hizmet bulunamıyorsa veya engellenemezse atabilirler. Genellikle WCF'de, bu durum istemciye istek-yanıttan daha hızlı dönen tek yönlü aramalarla sonuçlanır; ancak giden verilerin ağ üzerinden gönderilmesini yavaşlatan herhangi bir koşul, tek yönlü işlemlerin yanı sıra istek yanıtlama işlemlerini de yavaşlatıyor. Daha fazla bilgi için [WCF İstemci Kullanarak](./feature-details/accessing-services-using-a-client.md) [Tek Yönlü Hizmetler](./feature-details/one-way-services.md) ve Hizmetlere Erişim'e bakın.  
  
<a name="BKMK_q77"></a>
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Hizmetimde X.509 sertifikası kullanıyorum ve System.Security.Cryptography.CryptographicException alıyorum. Ne oluyor?  
 Bu genellikle IIS alt işleminin çalıştığı kullanıcı hesabını değiştirdikten sonra oluşur. Örneğin, Windows XP'de Aspnet_wp.exe'nin altında çalıştığı varsayılan kullanıcı hesabını ASPNET'ten özel bir kullanıcı hesabına değiştirirseniz, bu hatayı görebilirsiniz. Özel bir anahtar kullanıyorsanız, bu anahtarı depolayan dosyaya erişmek için izinlere sahip olması gerekir.  
  
 Bu durumda, özel anahtarı içeren dosya için işlemin hesabına okuma erişimi ayrıcalıkları vermeniz gerekir. Örneğin, IIS alt işlemi Bob hesabı altında çalışıyorsa, Bob'a özel anahtarı içeren dosyaya okuma erişimi vermeniz gerekir.  
  
 Belirli bir X.509 sertifikası için özel anahtarı içeren dosyaya doğru kullanıcı hesabına erişim innasıl verilebildiği hakkında daha fazla bilgi için [bkz.](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md)  
  
<a name="BKMK_q88"></a>
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Bir işlemin ilk parametresini büyük harften küçük harfe değiştirdim; Şimdi müvekkilim bir istisna atıyor. Ne oluyor?  
 İşlem imzasındaki parametre adlarının değerleri sözleşmenin bir parçasıdır ve büyük/küçük harf duyarlıdır. <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> Yerel parametre adı ile istemci uygulamaları için işlemi açıklayan meta verileri birbirinden ayırmanız gerektiğinde özniteliği kullanın.  
  
<a name="BKMK_q99"></a>
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Benim izleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException olsun. Ne oluyor?  
 Sistem tarafından sağlanan WCF izleme mekanizması olmayan bir izleme aracı kullanıyorsanız <xref:System.ServiceModel.EndpointNotFoundException> ve bir adres filtresi uyuşmazlığı olduğunu gösteren bir <xref:System.ServiceModel.Description.ClientViaBehavior> izleme aracı alırsanız, iletileri izleme yardımcı programına yönlendirmek için sınıfı kullanmanız ve yardımcı programın bu iletileri hizmet adresine yönlendirmesini sağlamanız gerekir. Sınıf, <xref:System.ServiceModel.Description.ClientViaBehavior> adresüstle belirtilen bir sonraki ağ adresini nihai alıcıdan ayrı olarak belirtmek için `Via` adres üstbilgisini `To` değiştirir. Ancak, bunu yaparken, değeri oluşturmak için kullanılan bitiş noktası `To` adresini değiştirmeyin.  
  
 Aşağıdaki kod örneği bir örnek istemci yapılandırma dosyasını gösterir.  
  
```xml
<endpoint
  address="http://localhost:8000/MyServer/"  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Temel adres nedir? Bitiş noktası adresiyle ne ilgisi var?  
 Temel adres, bir <xref:System.ServiceModel.ServiceHost> sınıfın kök adresidir. Varsayılan olarak, hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırmanıza bir sınıf eklerseniz, ana bilgisayar yayımları tüm uç noktalar için Web Hizmetleri Açıklama Dili (WSDL), http temel adresinden ve meta veri davranışına sağlanan göreli adreslerden artı "?wsdl" olarak alınır. ASP.NET ve IIS'yi biliyorsanız, temel adres sanal dizine eşdeğerdir.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>NetTcpBinding kullanarak bir hizmet bitiş noktası ile mex bitiş noktası arasında bağlantı noktası paylaşımı  
 Bir hizmetin temel adresini net.tcp://MyServer:8080/MyService olarak belirtir ve aşağıdaki uç noktaları eklerseniz:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 NetTcpBinding ayarlarından birini aşağıdaki yapılandırma snippet'inde gösterildiği gibi değiştirirseniz:  
  
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
  
 Aşağıdaki gibi bir hata göreceksiniz: İşlenmemiş Özel Durum: System.ServiceModel.AddressAlreadyInUseException: IP uç noktası 0.0.0.0:9000 üzerinde zaten bir dinleyici var farklı bir bağlantı noktası ile tam nitelikli bir URL belirterek bu hata nın üzerinde çalışabilirsiniz aşağıdaki yapılandırma snippet gösterildiği gibi MEX bitiş noktası:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>WCF SOAP uygulamasından WCF Web HTTP uygulamasını ararken hizmet aşağıdaki hatayı döndürür: 405 Yöntem İzin Verilmez  
 Bir WCF Web HTTP uygulamasını (wcf hizmetinden <xref:System.ServiceModel.WebHttpBinding> kullanan ve <xref:System.ServiceModel.Description.WebHttpBehavior>kullanan bir ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` hizmet) çağırmak aşağıdaki özel durumu oluşturabilir: Bu <xref:System.ServiceModel.OperationContext>özel durum, WCF'nin gelenlerle giden inin <xref:System.ServiceModel.OperationContext> üzerine yazması nedeniyle oluşur. Bu sorunu çözmek için, WCF Web HTTP hizmet işlemi içinde bir <xref:System.ServiceModel.OperationContextScope> oluşturun. Örnek:  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Kimlik Doğrulama Hatalarını Ayıklama](./feature-details/debugging-windows-authentication-errors.md)
