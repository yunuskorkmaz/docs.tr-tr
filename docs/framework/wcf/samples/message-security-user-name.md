---
title: İleti Güvenliği Kullanıcı Adı
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 783969342f007895016ed4183257d6b24188d76c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584733"
---
# <a name="message-security-user-name"></a>İleti Güvenliği Kullanıcı Adı
Bu örnek, istemci için Kullanıcı adı kimlik doğrulamasıyla WS-Security kullanan bir uygulamanın nasıl uygulanacağını gösterir ve sunucunun X. 509v3 sertifikasını kullanarak sunucu kimlik doğrulaması gerektirir. İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir. Varsayılan olarak, istemci tarafından sağlanan Kullanıcı adı ve parola geçerli bir Windows hesabında oturum açmak için kullanılır. Bu örnek, [WSHttpBinding](wshttpbinding.md)' i temel alır. Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programından (Client. exe) ve hizmet kitaplığından (Service. dll) oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnekte ayrıca şunları da gösterilmektedir:  
  
- Ek yetkilendirmenin gerçekleştirilebileceği şekilde, Windows hesaplarına varsayılan eşleme.  
  
- Hizmet kodundan Arayanın kimlik bilgilerine erişme.  
  
 Hizmet, Web. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bağlama, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) Varsayılan olarak ileti güvenliğini kullanan bir standart ile yapılandırılır. Bu örnek, standart [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) istemci Kullanıcı adı kimlik doğrulamasını kullanmak için standardı ayarlar. Davranış, hizmet kimlik doğrulaması için Kullanıcı kimlik bilgilerinin kullanılacağını belirtir. Sunucu sertifikası, içindeki özniteliğiyle ilgili konu adı için aynı değeri içermelidir `findValue` [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 İstemci uç noktası yapılandırması, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur. İstemci bağlama, uygun ve ile yapılandırılır `securityMode` `authenticationMode` . Bir çapraz bilgisayar senaryosunda çalışırken, hizmet uç noktası adresinin uygun şekilde değiştirilmesi gerekir.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 İstemci uygulama, kullanılacak kullanıcı adını ve parolayı ayarlar.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 MessageSecurity örneklerine eklenen Setup. bat toplu iş dosyası, sertifika tabanlı güvenlik gerektiren bir barındırılan uygulamayı çalıştırmak için sunucuyu ilgili sertifikayla yapılandırmanızı sağlar. Toplu iş dosyası iki modda çalıştırılabilir. Toplu iş dosyasını tek bilgisayar modunda çalıştırmak için `setup.bat` komut satırına yazın. Hizmet modu türünde çalıştırmak için `setup.bat service` . Bu modu, örneği bilgisayarlar arasında çalıştırırken kullanırsınız. Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.  
  
 Aşağıdakiler, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.  
  
- Sunucu sertifikası oluşturma  
  
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
  
     % SERVER_NAME% değişkeni sunucu adını belirtiyor. Sertifika, LocalMachine deposunda depolanır. Setup. bat toplu iş dosyası bir hizmet bağımsız değişkeniyle (gibi) çalışıyorsa% `setup.bat service` SERVER_NAME% bilgisayarın tam etki alanı adını içerir.  Aksi takdirde, varsayılan olarak localhost olur.  
  
- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme  
  
     Aşağıdaki satır, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Sertifikanın özel anahtarına izin verme  
  
     Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, ASP.NET çalışan işlem hesabına erişilebilen LocalMachine deposunda depolanan sunucu sertifikasını yapar.  
  
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
    > Windows 'un U. S. Ingilizce sürümünü kullanıyorsanız, Setup. bat dosyasını düzenlemeniz ve `NT AUTHORITY\NETWORK SERVICE` hesap adını bölgesel eşdeğerle değiştirmeniz gerekir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1. Yolun, MakeCert. exe ve FindPrivateKey. exe ' nin bulunduğu klasörü içerdiğinden emin olun.  
  
2. Yönetici ayrıcalıklarıyla açılan bir Geliştirici Komut İstemi Visual Studio için, örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.  
  
    > [!NOTE]
    > Setup. bat toplu iş dosyası, Visual Studio için Geliştirici Komut İstemi çalıştırılmak üzere tasarlanmıştır. PATH ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni, Visual Studio için bir Geliştirici Komut İstemi içinde otomatik olarak ayarlanır.  
  
3. Adresi girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın `http://localhost/servicemodelsamples/service.svc` .
  
4. \Client\bin. adresinden Client. exe ' yi Başlat İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
5. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Hizmet bilgisayarında bir dizin oluşturun. Internet Information Services yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.  
  
2. Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın. Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun. Ayrıca Setup. bat ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.  
  
3. İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.  
  
4. İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın. Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.  
  
5. Sunucusunda, `setup.bat service` yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi çalıştırın. `setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `service` bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
6. Web. config dosyasını, bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adını (serviceCertificate öğesinde bulunan findValue özniteliğinde) yansıtacak şekilde düzenleyin`.`  
  
7. Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
8. İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.  
  
9. İstemcide, yönetici ayrıcalıklarıyla açılan bir Geliştirici Komut İstemi Visual Studio için ImportServiceCert. bat dosyasını çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
10. İstemci bilgisayarda, bir komut isteminden Client. exe ' yi başlatın. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
  
    > [!NOTE]
    > Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .  
