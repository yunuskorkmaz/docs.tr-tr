---
title: İleti Güvenliği Sertifikası
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 92e656f36ae0af851def393575cbb7d418bc4a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183528"
---
# <a name="message-security-certificate"></a>İleti Güvenliği Sertifikası
Bu örnek, istemci için X.509 v3 sertifikası kimlik doğrulaması ile WS-Security kullanan bir uygulamanın nasıl uygulanacağını ve sunucunun X.509 v3 sertifikasını kullanarak sunucu kimlik doğrulamasını nasıl gerektirdiğini gösterir. Bu örnek, istemci ve sunucu arasındaki tüm uygulama iletilerinin imzalanıp şifrelenmiş olması için varsayılan ayarları kullanır. Bu örnek [WSHttpBinding'e](../../../../docs/framework/wcf/samples/wshttpbinding.md) dayanır ve bir istemci konsol programı ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığından oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Örnek, yapılandırmayı kullanarak kimlik doğrulamayı denetlemeyi ve aşağıdaki örnek kodda gösterildiği gibi, arayan kişinin kimliğinin güvenlik bağlamından nasıl alındığını gösterir.  

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
  
 Hizmet, yapılandırma dosyasını (Web.config) kullanılarak tanımlanan WS-MetadataExchange protokolünü kullanarak hizmetle iletişim kurmak için bir bitiş noktasını ve hizmetin WSDL belgesini ortaya çıkarmak için bir bitiş noktasını ortaya çıkarır. Bitiş noktası bir adres, bir bağlama ve sözleşmeden oluşur. Bağlama, ileti güvenliğini kullanmayı [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) varsayılan olarak varsayılan olarak standart bir ws://Binding>öğesi ile yapılandırılır. Bu örnek, `clientCredentialType` istemci kimlik doğrulaması gerektirecek şekilde Sertifika'ya özniteliği ayarlar.  
  
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
  
 Davranış, istemci hizmetin kimliğini doğruladığında kullanılan hizmetin kimlik bilgilerini belirtir. Sunucu sertifikası özne [ \<adı, hizmetKimlik Bilgileri>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) öğesindeki `findValue` öznitelikte belirtilir.  
  
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
  
 İstemci bitiş noktası yapılandırması, hizmet bitiş noktası, bağlama ve sözleşme için mutlak bir adresten oluşur. İstemci bağlama uygun güvenlik modu ve kimlik doğrulama modu ile yapılandırılır. Bir çapraz bilgisayar senaryosunda çalışırken, hizmet bitiş noktası adresinin buna göre değiştirildiğinden emin olun.  
  
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
  
 İstemci uygulaması, yapılandırma dosyası veya kod aracılığıyla sertifikayı kullanacak şekilde ayarlayabilir. Aşağıdaki örnek, sertifikanın yapılandırma dosyasında nasıl kullanılacağını gösterir.  
  
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
  
 Aşağıdaki örnek, programınızdaki hizmeti nasıl arayacağınızı gösterir.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 İleti Güvenliği örneklerine dahil olan Setup.bat toplu dosyası, istemci ve sunucuyu sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmanızı sağlar. Toplu iş dosyası üç modda çalıştırılabilir. Visual Studio için Geliştirici Komut Komut Usteminde tek bilgisayar modunda **setup.bat** türünde çalıştırmak için; servis modu türü **setup.bat hizmeti**için ; ve istemci modu türü **setup.bat istemcisi**için . Örneği bilgisayarlar arasında çalıştırırken istemci ve sunucu modunu kullanın. Ayrıntılar için bu konunun sonundaki kurulum yordamına bakın. Aşağıda, toplu iş dosyalarının uygun yapılandırmada çalışacak şekilde değiştirilebilmeleri için farklı bölümlerine kısa bir genel bakış sağlanacaktır:  
  
- İstemci sertifikasıoluşturma.  
  
     Toplu iş dosyasındaki aşağıdaki satır istemci sertifikasını oluşturur. Belirtilen istemci adı oluşturulan sertifikanın özne adında kullanılır. Sertifika mağaza da `My` `CurrentUser` depolanır.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- İstemci sertifikasını sunucunun güvenilir sertifika deposuna yükleme.  
  
     Toplu iş dosyasındaki aşağıdaki satır, istemci sertifikasını sunucunun Güvenilir Kişiler deposuna kopyalar, böylece sunucu ilgili güven veya güven siz kararları verebilir. Trusted People deposunda yüklü bir sertifikanın Bir Windows Communication Foundation (WCF) hizmeti tarafından güvenilebilmesi için `PeerOrChainTrust` istemci `PeerTrust`sertifikası doğrulama modunun ayarlanması veya 'ya ayarlanması gerekir. Yapılandırma dosyası kullanarak bunun nasıl yapılabileceğini öğrenmek için önceki hizmet yapılandırma örneğine bakın.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```  
  
- Sunucu sertifikası oluşturma.  
  
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
  
     %SERVER_NAME değişkeni sunucu adını belirtir. Sertifika LocalMachine mağazasında depolanır. Setup.bat toplu iş dosyası bir hizmet bağımsız değişkeni **(setup.bat hizmeti**gibi) ile çalıştırılırsa% SERVER_NAME%bilgisayarın tam nitelikli etki alanı adını içerir. Aksi takdirde varsayılan olarak localhost için.  
  
- Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme.  
  
     Aşağıdaki satır, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir. İstemci tarafından güvenilen kök sertifikasına dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- istemci sertifika deposunu sunucu sertifikasıyla doldurma adımı gerekli değildir.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Sertifikanın özel anahtarında izin verme.  
  
     Setup.bat dosyasındaki aşağıdaki satırlar, LocalMachine deposunda depolanan sunucu sertifikasını ASP.NET işiçin işiçin hesaba erişilebilir hale getirir.  
  
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
    > Windows'un ABD İngilizce olmayan bir sürümünü kullanıyorsanız, Setup.bat dosyasını düzenlemelisiniz ve "NT AUTHORITY\NETWORK SERVICE" hesap adını bölgesel eşdeğerinizle değiştirmeniz gerekir.  
  
> [!NOTE]
> Bu toplu iş dosyasında kullanılan araçlar C:\Program Files\Microsoft Visual Studio 8\Common7\tools veya C:\Program Files\Microsoft SDKs\Windows\v6.0\bin'de bulunur. Bu dizinlerden biri sistem yolunuzda olmalıdır. Visual Studio yüklüyse, bu dizini yolunuza almanın en kolay yolu Visual Studio için Geliştirici Komut Komut Ustem'ini açmaktır. **Başlat'ı**tıklatın ve ardından **Tüm Programlar**, Visual **Studio 2012**, **Araçlar**seçin. Bu komut istemi zaten yapılandırılmış uygun yolları vardır. Aksi takdirde, yolunuza el ile uygun dizin eklemeniz gerekir.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin:  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer alır:  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1. Yönetici ayrıcalıklarına sahip Visual Studio için bir Geliştirici Komut Komut Istem'i açın ve örnek yükleme klasöründen Setup.bat çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.  
  
    > [!NOTE]
    > Setup.bat toplu dosyası Visual Studio için Geliştirici Komut Komut Ustem'den çalıştırılmak üzere tasarlanmıştır. Yol ortamı değişkeninin SDK'nın yüklendiği dizine işaret etmesini gerektirir. Bu ortam değişkeni otomatik olarak Visual Studio için Geliştirici Komut Komut Istem (2010) içinde ayarlanır.  
  
2. Adresi `http://localhost/servicemodelsamples/service.svc`girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın.  
  
3. Client.exe'yi \client\bin'den başlatın. İstemci etkinliği istemci konsoluygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlarda çalıştırmak için  
  
1. Hizmet bilgisayarında bir dizin oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.  
  
2. Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples'ten hizmet bilgisayarındaki sanal dizine kopyalayın. \bin alt dizinindeki dosyaları kopyaladığınızdan emin olun. Ayrıca Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyalarını servis bilgisayarına kopyalayın.  
  
3. İstemci ikilileri için istemci bilgisayarında bir dizin oluşturun.  
  
4. İstemci programı dosyalarını istemci bilgisayarındaki istemci dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.  
  
5. Sunucuda, yönetici ayrıcalıklarına sahip Visual Studio için Geliştirici Komut Komut Ustem'de **setup.bat hizmetini** çalıştırın. Hizmet bağımsız **değişkeni** ile **setup.bat** çalıştıran bilgisayarın tam nitelikli etki alanı adı ile bir hizmet sertifikası oluşturur ve Service.cer adlı bir dosyaya hizmet sertifikası dışa aktarın.  
  
6. Web.config'i bilgisayarın tam nitelikli alan `findValue` adı ile aynı olan yeni sertifika adını [ \<(serviceCertificate>'daki ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)öznitelikte) yansıtacak şekilde edin.  
  
7. Service.cer dosyasını servis dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
8. İstemci de, yönetici ayrıcalıklarına sahip Visual Studio için Geliştirici Komut Komut Ustem'de **setup.bat istemcisini** çalıştırın. **Setup.bat'ı** **istemci** bağımsız değişkeniyle çalıştırmak, client.com adında bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarın.  
  
9. İstemci bilgisayarındaki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin. Bunu, localhost'u sunucunun tam nitelikli etki alanı adı ile değiştirerek yapın.  
  
10. Client.cer dosyasını istemci dizininden sunucudaki servis dizinine kopyalayın.  
  
11. İstemcide, yönetim ayrıcalıklarına sahip Visual Studio için Geliştirici Komut Komut Ustem'de ImportServiceCert.bat çalıştırın. Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.  
  
12. Sunucuda, yönetim ayrıcalıklarına sahip Visual Studio için Geliştirici Komut Komut Ustem'de ImportClientCert.bat çalıştırın. Bu, istemci sertifikasını Client.cer dosyasından LocalMachine - Trusted People deposuna aktarın.  
  
13. İstemci bilgisayarında, komut istemi penceresinden Client.exe'yi başlatın. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.  
  
    > [!NOTE]
    > Bu komut dosyası, bu örneği bilgisayarlar da çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
