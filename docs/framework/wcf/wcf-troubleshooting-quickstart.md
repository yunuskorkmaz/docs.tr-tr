---
title: WCF Sorun Giderme Hızlı Başlangıç
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 86aab2b39aaa9c7d7d92f7d5738482723cf6852f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320189"
---
# <a name="wcf-troubleshooting-quickstart"></a>WCF Sorun Giderme Hızlı Başlangıç
Bu konuda, müşterilerin, WCF istemcileri ve Hizmetleri geliştirirken çalıştırdığı bazı bilinen sorunlar listelenmektedir. Çalıştırmakta olduğunuz sorun bu listede yoksa, hizmetiniz için izlemeyi yapılandırmanızı öneririz. Bu, izleme dosyası görüntüleyiciyle görüntüleyebileceğiniz bir izleme dosyası oluşturur ve hizmet içinde oluşabilecek özel durumlar hakkında ayrıntılı bilgi edinebilirsiniz. İzlemeyi yapılandırma hakkında daha fazla bilgi için bkz: [Izlemeyi yapılandırma](./diagnostics/tracing/configuring-tracing.md). İzleme dosyası Görüntüleyicisi hakkında daha fazla bilgi için bkz. [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1. [Windows 7 ve IIS yükledikten sonra, bir WCF hizmetine gözatmaya çalıştıklarında şu hata iletisini alıyorum: HTTP hatası 404,3 – bulunamadı](#bkmk_0)  
  
     HTTP hatası 404,3 – bulunamadı sayfası uzantı yapılandırması nedeniyle sunulamıyor. Sayfa bir komut dosyası ise, bir işleyici ekleyin. Dosya indirildiyse, bir MIME eşlemesi ekleyin. Ayrıntılı hata InformationModule StaticFileModule.  
  
2. [Bazen, istemciniz ilk istekten sonraki bir sırada boşta kalırsa ikinci istekte bir MessageSecurityException aldım. Ne oluyor?](#BKMK_q1)  
  
3. [Hizmet, yaklaşık 10 istemci etkileşim kurduktan sonra yeni istemcileri reddedecek şekilde başlatılır. Ne oluyor?](#BKMK_q2)  
  
4. [Hizmet yapılandırmadan WCF uygulamasının yapılandırma dosyası dışında bir yerde yükleyebilir miyim?](#BKMK_q3)  
  
5. [Kullandığım hizmet ve istemci harika çalışıyor, ancak istemci başka bir bilgisayarda olduğunda bunları çalışmayacak mıyım? Ne oluyor?](#BKMK_q4)  
  
6. [Türün bir istisna olduğu bir FaultException @ no__t-1özel durumu >, genel tür değil, her zaman istemcide genel bir FaultException türü aldım. Ne oluyor?](#BKMK_q5)  
  
7. [Yanıt bir veri içerdiğinde tek yönlü ve istek-yanıt işlemleri kabaca aynı hızda döndürülür. Ne oluyor?](#BKMK_q6)  
  
8. [Kullandığım bir X. 509.440 sertifikası kullanıyorum ve bir System. Security. Cryptography. CryptographicException aldım. Ne oluyor?](#BKMK_q77)  
  
9. [Bir işlemin ilk parametresini büyük harften küçük harfe kadar değiştirdim; Artık istemcim bir özel durum oluşturuyor. Ne oluyor?](#BKMK_q88)  
  
10. [İzleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException aldım. Ne oluyor?](#BKMK_q99)  
  
11. [WCF SOAP uygulamasından bir WCF Web HTTP uygulaması çağrılırken hizmet şu hatayı döndürür: 405 yöntemine Izin verilmiyor](#BK_MK99)  
  
 [Temel adres nedir? Bir uç nokta adresiyle nasıl ilişki vardır?](#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Windows 7 ve IIS yükledikten sonra, bir WCF hizmetine gözatmaya çalıştıklarında şu hata iletisini alıyorum: HTTP hatası 404,3 – bulunamadı  
 Tam hata iletisi:  
  
 HTTP hatası 404,3 – bulunamadı sayfası uzantı yapılandırması nedeniyle sunulamıyor. Sayfa bir komut dosyası ise, bir işleyici ekleyin. Dosya indirildiyse, bir MIME eşlemesi ekleyin. Ayrıntılı hata InformationModule StaticFileModule.  
  
 Bu hata iletisi, "Windows Communication Foundation HTTP etkinleştirmesi" açıkça Denetim Masası 'nda ayarlanmamışsa oluşur. Bunu ayarlamak için, Denetim Masası 'na gidin, pencerenin sol alt köşesindeki Programlar ' a tıklayın. Windows özelliklerini aç veya Kapat ' a tıklayın. Microsoft .NET Framework 3.5.1 ' i genişletin ve Windows Communication Foundation HTTP etkinleştirmesi ' ni seçin.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Bazen, istemciniz ilk istekten sonraki bir sırada boşta kalırsa ikinci istekte bir MessageSecurityException aldım. Ne oluyor?  
 İkinci istek birincil olarak iki nedenden dolayı başarısız olabilir: (1) oturum zaman aşımına uğradı veya (2) hizmeti barındıran Web sunucusu geri dönüştürüldü. İlk durumda, oturum hizmetin zaman aşımına uğrayana kadar geçerli olur. Hizmet, hizmetin bağlamasında (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>) belirtilen süre içinde istemciden bir istek almadığında, hizmet güvenlik oturumunu sonlandırır. Sonraki istemci iletileri <xref:System.ServiceModel.Security.MessageSecurityException> ' a sonuçlanır. İstemci gelecek iletileri göndermek ya da durum bilgisi olan bir güvenlik bağlamı belirteci kullanmak için hizmetle güvenli bir oturum yeniden kurması gerekir. Durum bilgisi olan güvenlik bağlamı belirteçleri Ayrıca, güvenli bir oturumun, bir Web sunucusunun geri dönüştürülmekte olmasını sağlar. Güvenli bir oturumda durum bilgisi olan güvenli bağlam belirteçleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Alternatif olarak, güvenli oturumları devre dışı bırakabilirsiniz. [@No__t-1wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) bağlamayı kullandığınızda, güvenli oturumları devre dışı bırakmak için `establishSecurityContext` özelliğini `false` olarak ayarlayabilirsiniz. Diğer bağlamalara yönelik güvenli oturumları devre dışı bırakmak için özel bir bağlama oluşturmanız gerekir. Özel bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Bu seçeneklerden herhangi birini uygulamadan önce, uygulamanızın güvenlik gereksinimlerini anlamanız gerekir.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Hizmet, yaklaşık 10 istemci etkileşim kurduktan sonra yeni istemcileri reddedecek şekilde başlatılır. Ne oluyor?  
 Varsayılan olarak, hizmetlerde yalnızca 10 eşzamanlı oturum olabilir. Bu nedenle, hizmet bağlamaları oturumlar kullanıyorsa, hizmet bu sayıya ulaşana kadar yeni istemci bağlantılarını kabul eder ve ardından geçerli oturumlardan biri sonlanana kadar yeni istemci bağlantılarını reddeder. Birkaç yolla daha fazla istemci destekleyebilirsiniz. Hizmetiniz oturum gerektirmiyorsa, oturumsuz bağlama kullanmayın. (Daha fazla bilgi için bkz. [oturumları kullanma](using-sessions.md).) Diğer bir seçenek de <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> özelliğinin değerini, sizin için uygun olan sayı ile değiştirerek oturum sınırını artırmaya yönelik bir seçenektir.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Hizmet yapılandırmadan WCF uygulamasının yapılandırma dosyası dışında bir yerde yükleyebilir miyim?  
 Evet, ancak, <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yöntemini geçersiz kılan özel bir <xref:System.ServiceModel.ServiceHost> sınıfı oluşturmanız gerekir. Bu yöntemin içinde, önce yapılandırmayı yüklemek için temel çağırabilirsiniz (Standart yapılandırma bilgilerini de yüklemek istiyorsanız), ancak yapılandırma yükleme sistemini tamamen değiştirebilirsiniz. Yapılandırmayı uygulama yapılandırma dosyasından farklı bir yapılandırma dosyasından yüklemek isterseniz, yapılandırma dosyasını kendiniz ayrıştırabilmeniz ve yapılandırmayı yüklemeniz gerekir.  
  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yönteminin nasıl geçersiz kılınacağını ve bir uç noktanın doğrudan nasıl yapılandırılacağını gösterir.  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Kullandığım hizmet ve istemci harika çalışıyor, ancak istemci başka bir bilgisayarda olduğunda bunları çalışmayacak mıyım? Ne oluyor?  
 Özel duruma bağlı olarak birkaç sorun olabilir:  
  
- İstemci uç noktası adreslerini "localhost" değil ana bilgisayar adıyla değiştirmeniz gerekebilir.  
  
- Bağlantı noktasını uygulamaya açmanız gerekebilir. Ayrıntılar için bkz. SDK örneklerinden [güvenlik duvarı yönergeleri](./samples/firewall-instructions.md) .  
  
- Olası diğer sorunlar için [Windows Communication Foundation Örnekleri çalıştıran](./samples/running-the-samples.md)örnekler konusuna bakın.  
  
- İstemciniz Windows kimlik bilgilerini kullanıyorsa ve özel durum bir <xref:System.ServiceModel.Security.SecurityNegotiationException> ise, Kerberos 'u aşağıdaki şekilde yapılandırın.  
  
    1. Kimlik bilgilerini istemcinin App. config dosyasındaki Endpoint öğesine ekleyin:  
  
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
  
    2. Şirket içinde barındırılan hizmeti sistem veya NetworkService hesabı altında çalıştırın. Sistem hesabı altında bir komut penceresi oluşturmak için bu komutu çalıştırabilirsiniz:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. Hizmeti, varsayılan olarak hizmet asıl adı (SPN) hesabını kullanan Internet Information Services (IIS) altında barındırın.  
  
    4. SetSPN kullanarak etki alanı ile yeni bir SPN kaydettirin. Bunu yapmak için, bir etki alanı yöneticisi olmanız gerektiğini unutmayın.  
  
 Kerberos protokolü hakkında daha fazla bilgi için bkz. [WCF 'de kullanılan güvenlik kavramları](./feature-details/security-concepts-used-in-wcf.md) ve:  
  
- [Windows Kimlik Doğrulama Hatalarını Ayıklama](./feature-details/debugging-windows-authentication-errors.md)  
  
- [Http. sys kullanarak Kerberos hizmet sorumlusu adlarını kaydetme](https://go.microsoft.com/fwlink/?LinkId=86943)  
  
- [Açıklanan Kerberos](https://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Türün bir özel durum olduğu bir FaultException @ no__t-0Exception > oluştururken, genel tür değil, her zaman istemcide genel bir FaultException türü aldım. Ne oluyor?  
 Kendi özel hata veri türünü oluşturmanız ve bunu hata sözleşmenizin ayrıntı türü olarak bildirmeniz önemle tavsiye edilir. Nedeni sistem tarafından sağlanmış özel durum türlerini kullanmaktır:  
  
- Hizmet odaklı uygulamaların en büyük güçlerinden birini kaldıran bir tür bağımlılığı oluşturur.  
  
- Standart bir şekilde özel durum serileştirilme bağımlıdır. Bazıları — <xref:System.Security.SecurityException> — gibi, seri hale getirilebilir.  
  
- İstemcilere iç uygulama ayrıntılarını sunar. Daha fazla bilgi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Ancak bir uygulamada hata ayıklaması yapıyorsanız, özel durum bilgilerini seri hale getirebilirsiniz ve <xref:System.ServiceModel.Description.ServiceDebugBehavior> sınıfını kullanarak istemciye döndürebilirsiniz.  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Yanıt bir veri içerdiğinde tek yönlü ve istek-yanıt işlemleri kabaca aynı hızda döndürülür. Ne oluyor?  
 Bir işlemin tek bir şekilde belirtilmesi, yalnızca işlem sözleşmesinin bir giriş iletisini kabul ettiği ve bir çıkış iletisi döndürmediği anlamına gelir. WCF 'de, giden veriler kabloya yazıldığında veya bir özel durum oluştuğunda tüm istemci etkinleştirmeleri döndürülür. Tek yönlü işlemler aynı şekilde çalışır ve hizmet, ağdaki verileri kabul etmek üzere hazırlanmamışsa, hizmet bulunamıyorsa veya engellenmiyor olabilir. Genellikle WCF 'de, bu, istemciye istek yanıtlamadan daha hızlı dönen tek yönlü çağrılara neden olur; Ancak, giden verilerin ağ üzerinden gönderilmesini yavaşlatan herhangi bir koşul, tek yönlü işlemlerin yanı sıra istek-yanıt işlemlerini yavaşlatır. Daha fazla bilgi için bkz. [tek yönlü hizmetler](./feature-details/one-way-services.md) ve [WCF Istemcisi kullanarak hizmetlere erişme](./feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Kullandığım bir X. 509.440 sertifikası kullanıyorum ve bir System. Security. Cryptography. CryptographicException aldım. Ne oluyor?  
 Bu, genellikle IIS çalışan işleminin çalıştırıldığı Kullanıcı hesabı değiştirildikten sonra oluşur. Örneğin, [!INCLUDE[wxp](../../../includes/wxp-md.md)] ' da, Aspnet_wp. exe ' nin altında çalıştığı varsayılan kullanıcı hesabını özel bir kullanıcı hesabına değiştirirseniz, bu hatayı görebilirsiniz. Özel anahtar kullanılıyorsa, onu kullanan işlemin bu anahtarı depolayan dosyaya erişmek için gerekli izinlere sahip olması gerekir.  
  
 Bu durumda, özel anahtarı içeren dosya için işlem hesabına yönelik okuma erişim ayrıcalıklarına sahip olmanız gerekir. Örneğin, IIS çalışan işlemi Bob hesabı altında çalışıyorsa, Bob 'un özel anahtarı içeren dosyaya okuma erişimi vermesi gerekir.  
  
 Belirli bir X. 509.952 sertifikası için özel anahtarı içeren dosyaya doğru Kullanıcı hesabına erişim verme hakkında daha fazla bilgi için bkz. [nasıl yapılır: X. 509.440 SERTIFIKALARıNı WCF 'ye erişilebilir hale getirme](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Bir işlemin ilk parametresini büyük harften küçük harfe kadar değiştirdim; Artık istemcim bir özel durum oluşturuyor. Ne oluyor?  
 İşlem imzasında parametre adlarının değeri sözleşmenin bir parçasıdır ve büyük/küçük harfe duyarlıdır. Yerel parametre adı ile istemci uygulamaları için işlemi açıklayan meta veriler arasında ayrım yapmanız gerektiğinde <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> özniteliğini kullanın.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>İzleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException aldım. Ne oluyor?  
 Sistem tarafından sağlanmış WCF izleme mekanizması olmayan bir izleme aracı kullanıyorsanız ve bir adres filtresi uyumsuzluğu olduğunu belirten bir <xref:System.ServiceModel.EndpointNotFoundException> alırsanız, iletileri izleme yardımcı programına yönlendirmek için <xref:System.ServiceModel.Description.ClientViaBehavior> sınıfını kullanmanız gerekir ve yardımcı program bu iletileri hizmet adresine yeniden yönlendirir. @No__t-0 sınıfı, sonraki ağ adresini, `To` adresleme üstbilgisiyle belirtilen son alıcıdan ayrı olarak belirtmek için `Via` adresleme üst bilgisini değiştirir. Ancak bunu yaparken, `To` değerini oluşturmak için kullanılan uç nokta adresini değiştirmeyin.  
  
 Aşağıdaki kod örneği bir örnek istemci yapılandırma dosyası gösterir.  
  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Temel adres nedir? Bir uç nokta adresiyle nasıl ilişki vardır?  
 Temel adres, <xref:System.ServiceModel.ServiceHost> sınıfının kök adresidir. Varsayılan olarak, hizmet yapılandırmanıza bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sınıfı eklerseniz, ana bilgisayar yayımladığı tüm uç noktalar için Web Hizmetleri Açıklama Dili (WSDL) HTTP temel adresinden alınır ve meta veri davranışına ve "? wsdl ". ASP.NET ve IIS hakkında bilgi sahibiyseniz, taban adresi sanal dizine eşdeğerdir.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>NetTcpBinding kullanarak bir hizmet uç noktası ve bir MEX uç noktası arasında bağlantı noktası paylaşma  
 Bir hizmetin temel adresini net. TCP:/sunucum: 8080/hizmetim olarak belirtirseniz ve aşağıdaki uç noktaları eklemek için:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 Ve NetTcpBinding ayarlarından birini aşağıdaki yapılandırma kod parçacığında gösterildiği gibi değiştirirseniz:  
  
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
  
 Şu şekilde bir hata görürsünüz: Işlenmeyen özel durum: System. ServiceModel. Addressalreadınuseexception: IP bağlantı noktası 0.0.0.0:9000 üzerinde bir dinleyici zaten var Aşağıdaki yapılandırma kod parçacığında gösterildiği gibi, MEX uç noktası:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>WCF SOAP uygulamasından bir WCF Web HTTP uygulaması çağrılırken hizmet şu hatayı döndürür: 405 yöntemine Izin verilmiyor  
 WCF Web HTTP uygulamasını çağırma (bir WCF hizmetinden <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior>) kullanan bir hizmet şu özel durumu oluşturabilir: `Unhandled Exception: System.ServiceModel.FaultException`1 [System. ServiceModel. ExceptionDetail]: uzak sunucu beklenmeyen bir yanıt döndürdü: (405) yöntemi değil İzin verildi. ' Bu özel durum, WCF giden <xref:System.ServiceModel.OperationContext> ' ü gelen <xref:System.ServiceModel.OperationContext> ile üzerine yazdığından oluşur. Bu sorunu çözmek için WCF Web HTTP hizmeti işlemi içinde <xref:System.ServiceModel.OperationContextScope> oluşturun. Örneğin:  
  
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
