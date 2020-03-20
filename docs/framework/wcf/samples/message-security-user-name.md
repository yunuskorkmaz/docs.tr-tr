---
title: İleti Güvenliği Kullanıcı Adı
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 62b6f24bab1c655038ad3295f5af3dee0fa198fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183505"
---
# <a name="message-security-user-name"></a>İleti Güvenliği Kullanıcı Adı
Bu örnek, istemci için kullanıcı adı kimlik doğrulaması ile WS-Security kullanan bir uygulamanın nasıl uygulanacağını ve sunucunun X.509v3 sertifikasını kullanarak sunucu kimlik doğrulamasını nasıl gerektirdiğini gösterir. İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir. Varsayılan olarak, istemci tarafından sağlanan kullanıcı adı ve parola geçerli bir Windows hesabına oturum açmak için kullanılır. Bu örnek [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md)dayanmaktadır. Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programı (Client.exe) ve bir hizmet kitaplığından (Service.dll) oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnek aynı zamanda şunları gösterir:  
  
- Ek yetkilendirme yapIlebilmek için Windows hesaplarına varsayılan eşleme.  
  
- Arayan kişinin kimlik bilgilerine hizmet kodundan nasıl erişilir?  
  
 Hizmet, Web.config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir bitiş noktasını ortaya çıkarır. Bitiş noktası bir adres, bir bağlama ve sözleşmeden oluşur. Bağlama, ileti güvenliğini kullanmak varsayılan standart [ \<bir wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)ile yapılandırılır. Bu örnek, istemci kullanıcı adı kimlik doğrulaması kullanmak için standart [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ayarlar. Davranış, kullanıcı kimlik bilgilerinin hizmet kimlik doğrulaması için kullanılacağını belirtir. Sunucu sertifikası, [ \<hizmetKimlik Bilgileri>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)özniteliği `findValue` yle özne adı için aynı değeri içermelidir.  
  
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
  
 İstemci bitiş noktası yapılandırması, hizmet bitiş noktası, bağlama ve sözleşme için mutlak bir adresten oluşur. İstemci bağlama uygun `securityMode` ve `authenticationMode`. Bir çapraz bilgisayar senaryosunda çalışırken, hizmet bitiş noktası adresi buna göre değiştirilmelidir.  
  
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
  
 İstemci uygulaması kullanılacak kullanıcı adını ve parolayı ayarlar.  

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

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 MessageSecurity örneklerine dahil olan Setup.bat toplu iş dosyası, sunucuyu sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için ilgili bir sertifikayla yapılandırmanızı sağlar. Toplu iş dosyası iki modda çalıştırılabilir. Toplu iş dosyasını tek bilgisayar modunda `setup.bat` çalıştırmak için komut satırına yazın. Hizmet modu türünde `setup.bat service`çalıştırmak için. Örneği bilgisayarlar da çalıştırırken bu modu kullanırsınız. Ayrıntılar için bu konunun sonundaki kurulum yordamına bakın.  
  
 Aşağıda, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.  
  
- Sunucu sertifikası oluşturma  
  
     Setup.bat toplu dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     %SERVER_NAME değişkeni sunucu adını belirtir. Sertifika LocalMachine mağazasında depolanır. Setup.bat toplu iş dosyası bir hizmet bağımsız değişkeni (örneğin) `setup.bat service`ile çalıştırılırsa %SERVER_NAME%bilgisayarın tam nitelikli etki alanı adını içerir.  Aksi takdirde varsayılan olarak localhost için.  
  
- Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme  
  
     Aşağıdaki satır, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir. İstemci tarafından güvenilen kök sertifikasına dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- istemci sertifika deposunu sunucu sertifikasıyla doldurma adımı gerekli değildir.  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Sertifikanın özel anahtarında izin verme  
  
     Setup.bat toplu iş dosyasındaki aşağıdaki satırlar, LocalMachine deposunda depolanan sunucu sertifikasını ASP.NET işiçin işiçin hesaba erişebiliyor.  
  
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
    > Windows'un ABD İngilizce olmayan bir sürümünü kullanıyorsanız, Setup.bat dosyasını düzenlemelisiniz ve `NT AUTHORITY\NETWORK SERVICE` hesap adını bölgesel eşdeğerinizle değiştirmelisiniz.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1. Yolun Makecert.exe ve FindPrivateKey.exe'nin bulunduğu klasörü içerdiğinden emin olun.  
  
2. Administrator ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut Komut Ustem komutdosyasındaki örnek yükleme klasöründen Setup.bat'ı çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.  
  
    > [!NOTE]
    > Setup.bat toplu dosyası Visual Studio için Geliştirici Komut Komut Ustem'den çalıştırılmak üzere tasarlanmıştır. Yol ortamı değişkeninin SDK'nın yüklendiği dizine işaret etmesini gerektirir. Bu ortam değişkeni, Visual Studio için Geliştirici Komut Komut Ustem içinde otomatik olarak ayarlanır.  
  
3. Adresi `http://localhost/servicemodelsamples/service.svc`girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın.
  
4. Client.exe'yi \client\bin'den başlatın. İstemci etkinliği istemci konsoluygulamasında görüntülenir.  
  
5. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlarda çalıştırmak için  
  
1. Hizmet bilgisayarında bir dizin oluşturun. Internet Bilgi Hizmetleri yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.  
  
2. Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples'ten hizmet bilgisayarındaki sanal dizine kopyalayın. \bin alt dizinindeki dosyaları kopyaladığınızdan emin olun. Ayrıca Setup.bat ve Cleanup.bat dosyalarını servis bilgisayarına kopyalayın.  
  
3. İstemci ikilileri için istemci bilgisayarında bir dizin oluşturun.  
  
4. İstemci programı dosyalarını istemci bilgisayarındaki istemci dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.  
  
5. Sunucuda, yönetici `setup.bat service` ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut Komut Ustem'de çalıştırın. Bağımsız değişkenle birlikte çalışmak, `setup.bat` bilgisayarın tam nitelikli etki alanı adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service.cer adlı bir dosyaya aktarın. `service`  
  
6. Bilgisayarın tam nitelikli etki alanı adı ile aynı olan yeni sertifika adını (serviceCertificate öğesindeki findValue özniteliğinde) yansıtacak şekilde Web.config'i edin`.`  
  
7. Service.cer dosyasını servis dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
8. İstemci bilgisayarındaki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin.  
  
9. İstemci de, yönetici ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut Komut Ustem'de ImportServiceCert.bat çalıştırın. Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.  
  
10. İstemci bilgisayarında, istemci.exe'yi komut isteminden başlatın. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.  
  
    > [!NOTE]
    > Bu komut dosyası, bu örneği bilgisayarlar da çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
