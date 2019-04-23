---
title: WCF Sorun Giderme Hızlı Başlangıç
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 4327e8bb07cb03a91f7384f7fe82bc2e47f6fcb9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320008"
---
# <a name="wcf-troubleshooting-quickstart"></a>WCF Sorun Giderme Hızlı Başlangıç
Bu konuda, birkaç müşteriler içine geliştirme WCF istemcileri ve Hizmetleri çalıştırdığınız bilinen sorunlar listelenmektedir. Çalıştırmakta olduğunuz sorun bu listede değilse, hizmetiniz için izleme yapılandırma öneririz. Bu işlem bir izleme dosyası oluşturur izleme dosyası Görüntüleyici ile birlikte görüntülemek ve bu özel durumları hakkında ayrıntılı bilgi almak hizmet içinde oluşabilecek. İzlemeyi yapılandırma hakkında daha fazla bilgi için bkz: [İzlemeyi Yapılandırma](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). İzleme dosyası Görüntüleyici hakkında daha fazla bilgi için bkz: [Hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1. [Bir WCF hizmetine göz atmak denediğinizde Windows 7 ve IIS yükledikten sonra aşağıdaki hata iletisini alıyorum: HTTP Hatası 404.3 – bulunamadı](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     HTTP Hatası 404.3 – değil istediğiniz FoundThe sayfası uzantısı yapılandırması nedeniyle hizmet olamaz. Sayfa bir komut dosyası ise, bir işleyici ekleyin. Dosyanın indirilmesi gerektiğini MIME eşleme ekleyin. Ayrıntılı hata InformationModule StaticFileModule.  
  
2. [İstemcim ilk isteğinden sonra bir süredir boşta kalırsa bazen bir MessageSecurityException ikinci istekte alıyorum. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3. [Hizmetimi yaklaşık 10 istemcileri ile etkileşim sonra yeni istemcileri Reddet başlar. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4. [Hizmet yapılandırma öğesinden yere WCF uygulamanın yapılandırma dosyası diğer yükleyebilir?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5. [Hizmetimi ve istemci harika, ancak istemci, başka bir bilgisayarda olduğunda bunları çalıştıramıyor musunuz? Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6. [Bir FaultException miyim throw zaman\<özel durum > türü bir özel durum olduğunda, her zaman istemci üzerindeki bir genel FaultException türü ve genel tür alıyorum. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7. [Bu tek yönlü gibi görünür ve yanıt veri içerdiğinde istek-yanıt operations yaklaşık aynı hızda döndürür. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8. [X.509 sertifikası ile Hizmetimi kullanıyorum ve bir System.Security.Cryptography.CryptographicException alıyorum. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [İlk parametre bir işlemin öğesinden büyük değiştirdim küçük harf çoğaltmak; artık istemcim bir özel durum oluşturur. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [My izleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException alıyorum. Ne oluyor?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [WCF Web HTTP uygulama bir WCF SOAP uygulamasından çağırırken hizmet aşağıdaki hatayı döndürür: 405 Yönteme izin verilmiyor](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [Taban adresi nedir? Bu uç nokta adresi için nasıl ilişkilidir?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Bir WCF hizmetine göz atmak denediğinizde Windows 7 ve IIS yükledikten sonra aşağıdaki hata iletisini alıyorum: HTTP Hatası 404.3 – bulunamadı  
 Tam hata iletisi şudur:  
  
 HTTP Hatası 404.3 – değil istediğiniz FoundThe sayfası uzantısı yapılandırması nedeniyle hizmet olamaz. Sayfa bir komut dosyası ise, bir işleyici ekleyin. Dosyanın indirilmesi gerektiğini MIME eşleme ekleyin. Ayrıntılı hata InformationModule StaticFileModule.  
  
 Bu hata iletisi, Denetim Masası'ndaki "Windows Communication Foundation HTTP etkinleştirme" açıkça ayarlanmadı oluşur. Bu Git Denetim Masası'na ayarlamak için pencerenin alt sol köşede Programlar'ı tıklatın. Kapatma Windows özellikleri veya Kapat'a tıklayın. Microsoft .NET Framework 3.5.1 genişletin ve Windows Communication Foundation HTTP etkinleştirme'yi seçin.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>İstemcim ilk isteğinden sonra bir süredir boşta kalırsa bazen bir MessageSecurityException ikinci istekte alıyorum. Ne oluyor?  
 İkinci istek, temelde iki nedenden dolayı başarısız olabilir: (1) oturum zaman aşımına uğradı veya (2 Web sunucusu hizmetini barındıran dönüştürülmeden. Bu durumda, oturum hizmeti zaman aşımına uğrayana kadar geçerlidir. Zaman hizmeti almaz istek istemciden hizmetin bağlamasında belirtilen süre içinde (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), hizmet güvenlik oturumu sona erer. Sonraki istemci iletileri neden <xref:System.ServiceModel.Security.MessageSecurityException>. İstemci, güvenli bir oturum gelecekteki iletileri göndermek veya bir durum bilgisi olan güvenlik bağlamı belirteci kullanmak için hizmet ile yeniden oluşturmanız gerekir. Durum bilgisi olan güvenlik bağlamı belirteçler dönüştürüldüğü bir Web sunucusu varlığını sürdürmesi güvenli bir oturum de olanak sağlar. Durum bilgisi olan güvenli içerik belirteçleri güvenli bir oturumda kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir güvenlik bağlamı oluşturmak için güvenli bir oturum belirteci](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Alternatif olarak, güvenli oturumlarını devre dışı bırakabilirsiniz. Kullanırken [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ayarlayabileceğiniz bağlamayı `establishSecurityContext` özelliğini `false` güvenli oturumlarını devre dışı bırakmak için. Güvenli oturumlar diğer bağlantılar için devre dışı bırakmak için özel bir bağlama oluşturmanız gerekir. Özel bağlama oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Bu seçeneklerden birini uygulamadan önce uygulamanızın güvenlik gereksinimlerini anlamanız gerekir.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Hizmetimi yaklaşık 10 istemcileri ile etkileşim sonra yeni istemcileri Reddet başlar. Ne oluyor?  
 Varsayılan olarak yalnızca 10 eşzamanlı oturum hizmeti olabilir. Hizmet bağlamaları oturumları kullanırsanız, daha sonra yeni istemci bağlantılarını biri geçerli oturum sona kadar reddederse, bu sayıyı ulaşana kadar bu nedenle, hizmetin yeni istemci bağlantılarını kabul eder. Çeşitli yollarla daha fazla istemciyi destekleyebileceği. Hizmetinizi oturumları gerektirmiyorsa kapatamaması bağlama kullanmayın. (Daha fazla bilgi için [oturumları kullanarak](../../../docs/framework/wcf/using-sessions.md).) Değerini değiştirerek oturum sınırını artırmak için başka bir seçenektir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> özelliği için durumda uygun sayısı.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Hizmet yapılandırma öğesinden yere WCF uygulamanın yapılandırma dosyası diğer yükleyebilir?  
 Evet, ancak, özel bir oluşturmak zorunda <xref:System.ServiceModel.ServiceHost> kılan sınıf <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yöntemi. Bu yöntem içinde (Standart yapılandırma bilgilerini de yüklemek istiyorsanız) ilk yapılandırmasını yüklemek için temel çağırabilirsiniz ancak sistemi yükleme yapılandırmasını da tamamen değiştirebilirsiniz. Uygulama yapılandırma dosyasından farklı bir yapılandırma dosyasındaki yapılandırma yüklemek istiyorsanız, gerekir kendiniz yapılandırma dosyasını ayrıştırma ve yapılandırmayı unutmayın.  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Hizmetimi ve istemci harika, ancak istemci, başka bir bilgisayarda olduğunda bunları çalıştıramıyor musunuz? Ne oluyor?  
 Özel duruma bağlı bağlı olarak, çeşitli sorunları olabilir:  
  
-   İstemci uç nokta adresleri değil "localhost" ve ana bilgisayar adı değiştirmeniz gerekebilir.  
  
-   Uygulama bağlantı noktasını açmanız gerekebilir. Ayrıntılar için bkz [güvenlik duvarı yönergeleri](../../../docs/framework/wcf/samples/firewall-instructions.md) gelen SDK örnekleri.  
  
-   Diğer olası sorunları için örnekleri konusuna [Windows Communication Foundation örneklerini çalıştırma](./samples/running-the-samples.md).  
  
-   İstemci, Windows kimlik bilgilerini kullanıyor ve özel durum bir <xref:System.ServiceModel.Security.SecurityNegotiationException>, Kerberos gibi yapılandırın.  
  
    1.  Kimlik, istemcinin App.config dosyasındaki endpoint öğesine ekleyin:  
  
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
  
    2.  Şirket içinde barındırılan hizmeti sistem veya ağ hizmeti hesabı altında çalıştırın. Sistem hesabı altında bir komut penceresi oluşturmak için bu komutu çalıştırabilirsiniz:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  ' % S'hizmeti altında Internet Information Services (varsayılan olarak, hizmet asıl adı (SPN) hesabı kullanır, IIS), barındırma.  
  
    4.  Bir yeni SPN SetSPN kullanarak etki alanı ile kaydedin. Bunu yapmak için bir etki alanı yöneticisi olması gerektiğine dikkat edin.  
  
 Kerberos protokolü hakkında daha fazla bilgi için bkz: [güvenlik kavramları wcf'de kullanılan](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) ve:  
  
-   [Windows Kimlik Doğrulama Hatalarını Ayıklama](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [Kerberos hizmet asıl adları Http.sys kullanarak kaydetme](https://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [Kerberos açıklaması](https://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Bir FaultException miyim throw zaman\<özel durum > türü bir özel durum olduğunda, her zaman istemci üzerindeki bir genel FaultException türü ve genel tür alıyorum. Ne oluyor?  
 Veri türüne dönüştürün ve hata sözleşmeniz ayrıntı türü olarak olduğunu bildirir, kendi özel hata oluşturma önemle tavsiye edilir. Neden olan sistem tarafından sağlanan özel durum türlerini kullanma:  
  
-   Hizmet odaklı uygulamalar güçlerini en büyük zorluklardan biri kaldıran bir türü bağımlılığı oluşturur.  
  
-   Standart bir biçimde seri hale getirme özel durum sırasında bağımlı olamaz. Bazı — gibi <xref:System.Security.SecurityException>— tüm serileştirilebilir olmayabilir.  
  
-   İç uygulama ayrıntıları istemcilerine kullanıma sunar. Daha fazla bilgi için [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Bir uygulamada hata ayıklama yaparsanız, ancak özel durum bilgilerini seri hale getirmek ve kullanarak istemciye Döndür <xref:System.ServiceModel.Description.ServiceDebugBehavior> sınıfı.  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Bu tek yönlü gibi görünür ve yanıt veri içerdiğinde istek-yanıt operations yaklaşık aynı hızda döndürür. Ne oluyor?  
 Bir işlem için bir yol olduğunu belirten yalnızca da işlem anlaşması bir giriş iletisi kabul eder ve bir çıkış iletisi döndürmeyen anlamına gelir. Giden veri kablo için yazılmış veya bir özel durum WCF'de, tüm istemci çağrılarını dönün. Hizmet bulunması veya hizmet ağdan gelen verileri kabul etmek için hazır değil durumunda engelleyin oldukları oluşturabilecek ve tek yönlü işlem aynı şekilde çalışır. Genellikle WCF, istemciye istek-yanıt daha hızlı döndüren tek yönlü çağrıları sonuçlanır; ancak giden veriler ağ üzerinden gönderme yavaşlatır herhangi bir koşul istek-yanıt işlemlerinin yanı sıra, tek yönlü işlem yavaşlatır. Daha fazla bilgi için [One-Way Hizmetleri](../../../docs/framework/wcf/feature-details/one-way-services.md) ve [WCF istemci kullanarak hizmetlere erişme](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>X.509 sertifikası ile Hizmetimi kullanıyorum ve bir System.Security.Cryptography.CryptographicException alıyorum. Ne oluyor?  
 Bu genellikle, IIS çalışan altında çalıştırma işlemi kullanıcı hesabı değiştirildikten sonra gerçekleşir. Örneğin, [!INCLUDE[wxp](../../../includes/wxp-md.md)], Aspnet_wp.exe ASPNET bir özel kullanıcı hesabına çalıştığı varsayılan kullanıcı hesabı değiştirirseniz, bu hatayı görebilirsiniz. Özel anahtarı kullanıyorsanız, bunu kullandığı işlem bu anahtarın depolandığı dosya erişim iznine sahip gerekecektir.  
  
 Bu durumda, özel anahtarı içeren dosyayı işlemin hesaba okuma erişimi ayrıcalıkları vermeniz gerekir. Örneğin, IIS çalışan işlemi Bob hesabı altında çalışıyorsa, bu özel anahtarı içeren dosyanın Bob okuma erişimi verin gerekecektir.  
  
 Belirli bir X.509 sertifikası özel anahtarı içeren dosyayı doğru kullanıcı hesabı erişimi vermek hakkında daha fazla bilgi için bkz. [nasıl yapılır: X.509 sertifikalarını WCF için erişilebilir duruma](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>İlk parametre bir işlemin öğesinden büyük değiştirdim küçük harf çoğaltmak; artık istemcim bir özel durum oluşturur. Ne oluyor?  
 Parametre adları işlemi imzasında değerini sözleşmenin bir parçası olan ve büyük küçük harfe duyarlıdır. Kullanım <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> yerel parametre adı ve istemci uygulamaları için işlem açıklayan meta veriler arasında ayrım yapmak, ihtiyacınız olduğunda özniteliği.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>My izleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException alıyorum. Ne oluyor?  
 Sistem tarafından sağlanan WCF izleme mekanizması değil bir izleme aracı kullanıyorsanız ve aldığınız bir <xref:System.ServiceModel.EndpointNotFoundException> belirten bir adres filtresi uyuşmazlığı oluştu, kullanmanız gereken <xref:System.ServiceModel.Description.ClientViaBehavior> izleme yardımcı programı iletileri yönlendirmek için sınıf ve Bu ileti hizmet adresine yönlendirmek yardımcı programı vardır. <xref:System.ServiceModel.Description.ClientViaBehavior> Sınıfı değiştirir `Via` adresleme üstbilgi listesinden ultimate alıcı, sonraki ağ adresini belirtmek için gösterilen `To` adresleme başlığı. Bunu yaparken kurmak için kullanılan uç nokta adresini ancak değiştirmeyin `To` değeri.  
  
 Aşağıdaki kod örneği, örnek istemci yapılandırma dosyası gösterir.  
  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Taban adresi nedir? Bu uç nokta adresi için nasıl ilişkilidir?  
 Kök adresidir temel adres bir <xref:System.ServiceModel.ServiceHost> sınıfı. Varsayılan olarak eklerseniz, bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> konak yayımlar tüm uç noktaları HTTP temel adresi yanı sıra, meta veri davranışı için sağlanan tüm göreli adres alınır için Web Hizmetleri Açıklama Dili (WSDL), hizmet yapılandırmasını sınıfı Ayrıca "? wsdl". Alışkın olduğunuz [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ve IIS temel adres sanal dizin ile eşdeğer.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Hizmet uç noktası ve NetTcpBinding kullanarak bir mex uç arasında bir bağlantı noktası paylaşımı  
 Net.tcp://MyServer bir hizmet için temel adresini belirtirseniz: 8080/Hizmetim ve aşağıdaki uç noktaların ekleyin:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 Ve NetTcpBinding ayarlardan biri aşağıdaki yapılandırma kod parçacığında gösterildiği gibi değiştirin:  
  
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
  
 Aşağıdaki gibi bir hata görürsünüz: İşlenmeyen özel durum: System.ServiceModel.addressalreadyınuseexception: Zaten var. bir dinleyici IP uç noktası 0.0.0.0:9000 aşağıdaki yapılandırma kod parçacığında gösterildiği gibi MEX uç noktası için farklı bir bağlantı noktası ile tam bir URL belirterek bu hataya çalışabilir üzerinde:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>WCF Web HTTP uygulama bir WCF SOAP uygulamasından çağırırken hizmet aşağıdaki hatayı döndürür: 405 Yönteme izin verilmiyor  
 WCF Web HTTP uygulama çağırma (kullanan bir hizmet <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior>) bir WCF hizmeti şu özel durum oluşturabilir: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: Uzak sunucu beklenmeyen bir yanıt döndürdü: (405) yöntemi değil izin verilir.' WCF giden üzerine yazar. Bu özel durum oluşur <xref:System.ServiceModel.OperationContext> gelen ile <xref:System.ServiceModel.OperationContext>. Bu sorunu çözmek için oluşturma bir <xref:System.ServiceModel.OperationContextScope> WCF Web HTTP hizmeti işlemi içinde. Örneğin:  
  
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

- [Windows Kimlik Doğrulama Hatalarını Ayıklama](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
