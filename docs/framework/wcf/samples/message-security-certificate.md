---
title: İleti Güvenliği Sertifikası
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: bd84cb45de68ee86cb042e85695f4893c0ca6988
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424140"
---
# <a name="message-security-certificate"></a>İleti Güvenliği Sertifikası
Bu örnek, istemci için X. 509.440 v3 sertifika kimlik doğrulamasıyla WS-Security kullanan bir uygulamanın nasıl uygulanacağını gösterir ve sunucunun X. 509.440 v3 sertifikasını kullanarak sunucu kimlik doğrulaması gerektirir. Bu örnek, istemci ve sunucu arasındaki tüm uygulama iletilerinin imzalanıp şifrelendiğinden emin olmak için varsayılan ayarları kullanır. Bu örnek, [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) 'i temel alır ve Internet INFORMATION SERVICES (IIS) tarafından barındırılan bir istemci konsol programından ve bir hizmet kitaplığından oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Örnek, aşağıdaki örnek kodda gösterildiği gibi, yapılandırma ve arayanın kimliğini güvenlik bağlamdan alma ' yı kullanarak, kimlik doğrulamasının denetlenmesini gösterir.  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 Hizmet, hizmet ile iletişim kurmak için bir uç nokta ve yapılandırma dosyası (Web. config) kullanılarak tanımlanan WS-MetadataExchange protokolünü kullanarak hizmetin WSDL belgesini açığa çıkarmak için bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bağlama, varsayılan olarak ileti güvenliğini kullanan standart bir [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ile yapılandırılır. Bu örnek, istemci kimlik doğrulaması gerektirmek için `clientCredentialType` özniteliğini sertifikaya ayarlar.  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 Davranış, istemci hizmetin kimliğini doğruladığında kullanılan hizmetin kimlik bilgilerini belirtir. Sunucu sertifikası konu adı, [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) öğesindeki `findValue` özniteliğinde belirtilir.  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 İstemci uç noktası yapılandırması, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur. İstemci bağlama, uygun güvenlik modu ve kimlik doğrulama moduyla yapılandırılır. Bir çapraz bilgisayar senaryosunda çalışırken, hizmet uç noktası adresinin uygun şekilde değiştiğinden emin olun.  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 İstemci uygulama, yapılandırma dosyası ya da kod aracılığıyla sertifikayı kullanacak şekilde ayarlayabilir. Aşağıdaki örnek, yapılandırma dosyasında kullanılmak üzere sertifikanın nasıl ayarlanacağını gösterir.  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 Aşağıdaki örnek, programınızda hizmetin nasıl çağrılacağını gösterir.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Ileti güvenlik örneklerine eklenen Setup. bat toplu iş dosyası, sertifika tabanlı güvenlik gerektiren bir barındırılan uygulamayı çalıştırmak için istemciyi ve sunucuyu ilgili sertifikalarla yapılandırmanıza olanak sağlar. Toplu iş dosyası üç modda çalıştırılabilir. Visual Studio için Geliştirici Komut İstemi, tek bilgisayarlı modda çalıştırmak için **Setup. bat** yazın; hizmet modu için **Setup. bat hizmeti**; istemci modu için **Setup. bat client**yazın. Örneği bilgisayarlar arasında çalıştırırken istemci ve sunucu modunu kullanın. Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın. Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar:  
  
- İstemci sertifikası oluşturuluyor.  
  
     Toplu iş dosyasındaki aşağıdaki satır, istemci sertifikasını oluşturur. Belirtilen istemci adı, oluşturulan sertifikanın konu adı ' nda kullanılır. Sertifika, `CurrentUser` depolama konumunda `My` deposunda depolanır.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- İstemci sertifikası sunucunun Güvenilen sertifika deposuna yükleniyor.  
  
     Toplu iş dosyasında aşağıdaki satır, sunucunun ilgili güveni veya güven dışı kararlar verebilmeleri için istemci sertifikasını sunucunun Trustedkişiler deposuna kopyalar. Trustedkişiler deposuna yüklenmiş bir sertifikanın bir Windows Communication Foundation (WCF) hizmeti tarafından güvenilmesi için, istemci sertifikası doğrulama modunun `PeerOrChainTrust` veya `PeerTrust`olarak ayarlanması gerekir. Bunun bir yapılandırma dosyası kullanılarak nasıl yapılabileceğinizi öğrenmek için önceki hizmet yapılandırma örneğine bakın.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
- Sunucu sertifikası oluşturuluyor.  
  
     Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     % SERVER_NAME% değişkeni sunucu adını belirtiyor. Sertifika, LocalMachine deposunda depolanır. Setup. bat toplu iş dosyası bir hizmet bağımsız değişkeniyle (örneğin, **Setup. bat hizmeti**) ÇALıŞıYORSA% sunucu_adı% bilgisayarın tam etki alanı adını içerir. Aksi takdirde, varsayılan olarak localhost olur.  
  
- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.  
  
     Aşağıdaki satır, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Sertifikanın özel anahtarına izin veriliyor.  
  
     Setup. bat dosyasındaki aşağıdaki satırlar, LocalMachine deposunda depolanan sunucu sertifikasını ASP.NET çalışan işlem hesabına erişilebilir hale getirir.  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    > Windows 'un U. S. Ingilizce sürümünü kullanıyorsanız, Setup. bat dosyasını düzenlemeniz ve "NT AUTHORITY\NETWORK SERVICE" hesap adını bölgesel eşdeğerle değiştirmeniz gerekir.  
  
> [!NOTE]
> Bu toplu iş dosyasında kullanılan araçlar C:\Program Files\Microsoft Visual Studio 8 \ Common7\tools veya C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. dizininde bulunur. Bu dizinlerden biri sistem yolunuzda olmalıdır. Visual Studio yüklüyse, yolunuzda bu dizini almanın en kolay yolu Visual Studio için Geliştirici Komut İstemi açmanız gerekir. **Başlat**' a tıklayın ve ardından **tüm programlar**, **Visual Studio 2012**, **Araçlar**' ı seçin. Bu komut isteminde uygun yollar zaten yapılandırılmış. Aksi takdirde, uygun dizini yolunuza el ile eklemeniz gerekir.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin:  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek aşağıdaki dizinde bulunur:  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1. Yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.  
  
    > [!NOTE]
    > Setup. bat toplu iş dosyası, Visual Studio için Geliştirici Komut İstemi çalıştırılmak üzere tasarlanmıştır. PATH ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni, Visual Studio için bir Geliştirici Komut İstemi içinde otomatik olarak ayarlanır (2010).  
  
2. Adresi `http://localhost/servicemodelsamples/service.svc`girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın.  
  
3. \Client\bin. adresinden Client. exe ' yi Başlat İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Hizmet bilgisayarında bir dizin oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.  
  
2. Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın. Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun. Ayrıca Setup. bat, Cleanup. bat ve ImportClientCert. bat dosyalarını hizmet bilgisayarına kopyalayın.  
  
3. İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.  
  
4. İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın. Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.  
  
5. Sunucusunda, yönetici ayrıcalıklarına sahip bir Visual Studio için Geliştirici Komut İstemi **Setup. bat hizmetini** çalıştırın. **Setup. bat** dosyasını **hizmet** bağımsız değişkeniyle çalıştırmak, bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
6. Web. config dosyasını, bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adını ( [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)`findValue` özniteliğinde) yansıtacak şekilde düzenleyin.  
  
7. Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
8. İstemcisinde, yönetici ayrıcalıklarına sahip bir Visual Studio için Geliştirici Komut İstemi **Setup. bat istemcisini** çalıştırın. **Setup. bat** dosyasını **istemci** bağımsız değişkeniyle çalıştırmak, Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client. cer adlı bir dosyaya aktarır.  
  
9. İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. Localhost 'u sunucunun tam etki alanı adıyla değiştirerek bunu yapın.  
  
10. Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.  
  
11. İstemcisinde, yönetim ayrıcalıklarına sahip bir Visual Studio için Geliştirici Komut İstemi ImportServiceCert. bat dosyasını çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
12. Sunucusunda, yönetim ayrıcalıklarına sahip bir Visual Studio için Geliştirici Komut İstemi ImportClientCert. bat dosyasını çalıştırın. Bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.  
  
13. İstemci bilgisayarda, bir komut istemi penceresinden Client. exe ' yi başlatın. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
  
    > [!NOTE]
    > Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
