---
title: İleti Güvenliği Kullanıcı Adı
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: c8be13743de6110658588aa983fd5da0397c5cb0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183431"
---
# <a name="message-security-user-name"></a>İleti Güvenliği Kullanıcı Adı
Bu örnek, kullanıcı adı kimlik doğrulaması için istemci ile WS-güvenlik kullanan ve sunucusunun X.509v3 sertifikasını kullanarak kimlik doğrulaması gerektiren bir uygulamanın nasıl uygulanacağını gösterir. Tüm uygulama iletileri istemci ve sunucu arasında imzalanmış ve şifrelenmiş. Varsayılan olarak, kullanıcı adı ve parolanızı, istemci tarafından kullanılan oturum açmak için geçerli bir Windows hesabı. Bu örnek dayanır [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md). Bu örnek, bir istemci konsol programı'nı (Client.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (Service.dll) oluşur. Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek ayrıca gösterir:  
  
-   Ek yetkilendirme gerçekleştirilebilir için varsayılan Windows hesaplarına eşlemesi.  
  
-   Arayanın kimlik bilgileri hizmet kodundan erişim yapma.  
  
 Hizmet, Web.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar. Uç nokta, adres, bağlama ve bir sözleşme oluşur. Bir standart yapılandırılmış bağlama [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), bunun varsayılan ileti güveliği kullanarak için. Bu örnek, standart ayarlar [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) istemci kullanıcı adı kimlik doğrulaması kullanmak için. Davranış hizmeti kimlik doğrulaması için kullanılacak olan kullanıcı kimlik bilgilerini belirtir. Sunucu sertifikasının konu adı olarak aynı değeri içermelidir `findValue` özniteliğini [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
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
  
 İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin oluşur. Bağlama istemcinin uygun olarak yapılandırıldığı `securityMode` ve `authenticationMode`. Bilgisayarlar arası senaryoda çalıştırırken, hizmet uç noktası adresi uygun şekilde değiştirilmesi gerekir.  
  
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
  
 İstemci uygulaması, kullanıcı adını ve parolayı ayarlar.  

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

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 MessageSecurity örnekleriyle dahil Setup.bat toplu iş dosyası sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için ilgili bir sertifika sunucusu yapılandırmanızı sağlar. Toplu iş dosyasını iki modda çalıştırabilirsiniz. Tek bilgisayarlı modunda toplu iş dosyasını çalıştırmak için şunu yazın `setup.bat` komut satırına. Hizmet modu türü içinde çalıştırmak için `setup.bat service`. Örnek bilgisayarlar arasında çalıştırırken bu modu kullanın. Ayrıntılar için bu konunun sonunda Kurulum yordamına bakın.  
  
 Toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.  
  
-   Sunucu sertifikası oluşturma  
  
     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     % Sunucu_adı % değişkeni, sunucu adını belirtir. Depolanmış bir sertifikayla LocalMachine depolama. Setup.bat toplu iş dosyasını hizmet bağımsız değişkenlerle çalıştırırsanız (gibi `setup.bat service`) sunucu_adı % bilgisayarın tam etki alanı adını içerir.  Aksi takdirde localhost için varsayılan olarak.  
  
-   İstemcinin güvenilen sertifika deposuna sunucu sertifikası yükleme  
  
     Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Sertifikanın özel anahtarı izin verme  
  
     Sunucu sertifikası için erişilebilir LocalMachine deposunda depolanır Setup.bat toplu iş dosyasında aşağıdaki satırları olun [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] çalışan işlem hesabı.  
  
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
    >  ABD dışı kullanıyorsanız Setup.bat dosyasını düzenleyin ve yerini Windows İngilizce sürümünü `NT AUTHORITY\NETWORK SERVICE` , bölgesel karşılığı hesap adıyla.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1.  Yolun Makecert.exe ve FindPrivateKey.exe bulunduğu klasörü içerdiğinden emin olun.  
  
2.  Yönetici ayrıcalıklarıyla açılan bir Visual Studio komut istemi örnek yükleme klasöründe Setup.bat çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası, bir Visual Studio komut isteminden çalıştırılması için tasarlanmıştır. Bu, path ortam değişkenine'nın SDK'ın yüklendiği dizini gösterecek gerektirir. Bu ortam değişkeni, bir Visual Studio komut istemi içinde otomatik olarak ayarlanır.  
  
3.  Adresini girerek bir tarayıcı kullanarak hizmetine erişiminizi doğrulayın `http://localhost/servicemodelsamples/service.svc`.
  
4.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
5.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda bir dizin oluşturun. Internet Information Services yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.  
  
2.  Hizmet program dosyaları \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın. Dosyaları \bin alt dizinde kopyalama emin olun. Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.  
  
3.  İstemci ikili dosyaları için istemci bilgisayarda bir dizin oluşturun.  
  
4.  İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.  
  
5.  Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.  
  
6.  Bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adı (serviceCertificate öğesindeki findValue özniteliği) yansıtacak şekilde Web.config Düzenle`.`  
  
7.  Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.  
  
8.  İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.  
  
9. İstemcide ImportServiceCert.bat yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminde çalıştırın. Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.  
  
10. İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
-   Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
    > [!NOTE]
    >  Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Ayrıca Bkz.
