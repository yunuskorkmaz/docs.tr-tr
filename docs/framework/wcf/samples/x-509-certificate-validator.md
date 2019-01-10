---
title: X.509 Sertifika Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: f8bc5c1976e61cbb81d0bc8463a57cfad750a2a7
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030314"
---
# <a name="x509-certificate-validator"></a>X.509 Sertifika Doğrulayıcı
Bu örnek bir özel X.509 Sertifika Doğrulayıcı uygulama gösterir. Bu, yerleşik X.509 Sertifika doğrulama modları hiçbiri uygulama gereksinimlerini için uygun olduğu durumlarda kullanışlıdır. Bu örnek, şirket içinde verilen sertifikaları kabul eden özel Doğrulayıcı sağlayıcısı olan bir hizmete gösterir. İstemci hizmete kimlik doğrulaması için bu tür bir sertifika kullanır.

 Not: Hizmet tarafından kullanılan özel Doğrulayıcı ChainTrust X509CertificateValidationMode tarafından sağlanan varsayılan davranışını daha az güvenli aynıdır herkes kendi kendine verilen bir sertifika oluşturabilirsiniz. Bu güvenlik kapsamı, üretim kodunda bu doğrulama mantığı kullanmadan önce dikkatle düşünülmelidir.

 Özet olarak, bu örnek gösterir nasıl:

-   İstemci, bir X.509 sertifikası kullanılarak doğrulanabilir.

-   Sunucu, istemci kimlik bilgileri özel X509CertificateValidator karşı doğrular.

-   Sunucu sunucusunun X.509 sertifikasını kullanarak kimlik doğrulaması yapılır.

 Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar. Uç nokta, adres, bağlama ve bir sözleşme oluşur. Bir standart yapılandırılmış bağlama `wsHttpBinding` varsayılanları kullanarak `WSSecurity` ve istemci sertifikası kimlik doğrulaması. Hizmet davranışı, Doğrulayıcı sınıfını türü ile birlikte istemci X.509 sertifikalarını doğrulamak için özel modunu belirtir. Davranış da serviceCertificate öğesini kullanarak sunucu sertifikasını belirtir. Sunucu sertifikası için aynı değeri içermesi gerekir `SubjectName` olarak `findValue` içinde [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

```xml
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- use host/baseAddresses to configure base address -->
        <!-- provided by host -->
        <host>
          <baseAddresses>
            <add baseAddress =
                "http://localhost:8001/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address specified above, provide one endpoint -->
        <endpoint address="certificate"
               binding="wsHttpBinding"
               bindingConfiguration="Binding"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <!-- X509 certificate binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults ="true"/>
          <serviceCredentials>
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

 İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin bir yapılandırma adı oluşur. Bağlama istemcinin uygun modu ve şu iletiyle yapılandırıldığı `clientCredentialType`.

```xml
<system.serviceModel>
    <client>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
        address=
        "http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>
    <bindings>
        <wsHttpBinding>
            <!-- X509 certificate binding -->
            <binding name="Binding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
               </security>
            </binding>
       </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- PeerOrChainTrust means that if the certificate -->
              <!-- is in the user's Trusted People store, then it -->
              <!-- is trusted without performing a validation of -->
              <!-- the certificate's issuer chain. -->
              <!-- This setting is used here for convenience so -->
              <!-- that the sample can be run without having to -->
              <!-- have certificates issued by a certification -->
              <!-- authority (CA). This setting is less secure -->
              <!-- than the default, ChainTrust. The security -->
              <!-- implications of this setting should be -->
              <!-- carefully considered before using -->
              <!-- PeerOrChainTrust in production code.-->
              <authentication
                  certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>
```

 İstemci uygulaması, istemci sertifikasını kullanmak için ayarlar.

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client = new CalculatorClient("Certificate");
try
{
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
    client.Close();
}
catch (TimeoutException e)
{
    Console.WriteLine("Call timed out : {0}", e.Message);
    client.Abort();
}
catch (CommunicationException e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
```

 Bu örnek bir özel X509CertificateValidator sertifikalarını doğrulamak için kullanır. Öğesinden türetilen CustomX509CertificateValidator, örnek uygulayan <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Belgelere bakın <xref:System.IdentityModel.Selectors.X509CertificateValidator> daha fazla bilgi için. Bu belirli özel Doğrulayıcı sağlayıcısı örnek, aşağıdaki kodda gösterildiği gibi şirket içinde verilen herhangi bir X.509 sertifikası kabul etmek için Doğrula yöntemini uygular.

```csharp
public class CustomX509CertificateValidator : X509CertificateValidator
{
  public override void Validate ( X509Certificate2 certificate )
  {
   // Only accept self-issued certificates
   if (certificate.Subject != certificate.Issuer)
     throw new Exception("Certificate is not self-issued");
   }
}
```

 Doğrulayıcı hizmeti kodunda uygulandıktan sonra hizmet ana bilgisayarı kullanmak için Doğrulayıcı örneği hakkında bilgilendirilmesi gerekir. Bu yapılır aşağıdaki kodu kullanarak.

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 Ya da aynı şeyi yapılandırmasında şu şekilde yapabilirsiniz.

```xml
<behaviors>
    <serviceBehaviors>
     <behavior name="CalculatorServiceBehavior">
       ...
   <serviceCredentials>
    <!--The serviceCredentials behavior allows one to specify -->
    <!--authentication constraints on client certificates.-->
    <clientCertificate>
    <!-- Setting the certificateValidationMode to Custom means -->
    <!--that if the custom X509CertificateValidator does NOT -->
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci başarıyla tüm yöntemlerini çağırmanız gerekir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Kurulum toplu iş dosyası
 Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:

-   Sunucu sertifikası oluşturuluyor:

     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun. % Sunucu_adı % değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Localhost varsayılan değerdir.

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor:

     İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. MakeCert.exe tarafından oluşturulan sertifikaları istemci sistem tarafından örtük olarak güvenilmeyen olduğundan bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   İstemci sertifikası oluşturma:

     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak istemci sertifikası oluşturun. % Değişken % USER_NAME istemci adını belirtir. Bu istemci kodu arar adı olduğundan, bu değer "test1" için ayarlanır. USER_NAME % değerini değiştirirseniz Client.cs kaynak dosyasında karşılık gelen değeri değiştirin ve istemciyi yeniden oluşturun.

     Sertifika CurrentUser depolama konumu altında (Kişisel) My deposunda depolanır.

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

-   İstemci sertifikası sunucusunun güvenilen sertifika depolama alanına yükleme:

     Setup.bat toplu iş dosyasında aşağıdaki satırları istemci sertifikası güvenilir Kişiler deposuna kopyalar. MakeCert.exe tarafından oluşturulan sertifikaları sunucu sistem tarafından örtük olarak güvenilmeyen olduğundan bu adım gereklidir. Bir güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — istemci sertifikası ile sunucu sertifika deposuna yerleştirmek, bu adım gerekli değildir.

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için

1.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

2.  Bir tek - veya çapraz-computerconfiguration içinde örneği çalıştırmak için aşağıdaki yönergeleri kullanın.

#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1.  Visual Studio 2012 komut istemini yönetici ayrıcalıklarıyla açılan içinde örnek yükleme klasöründen Setup.bat çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.

    > [!IMPORTANT]
    >  Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır. PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın.  
  
2.  Service.exe service\bin ' başlatın.  
  
3.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda bir dizin oluşturun.  
  
2.  Hizmet program dosyaları \service\bin hizmeti bilgisayarında sanal dizinine kopyalayın. Ayrıca hizmet bilgisayara Setup.bat, Cleanup.bat GetComputerName.vbs ve ImportClientCert.bat dosyaları kopyalayın.  
  
3.  Bir dizin üzerinde istemci computerfor istemci ikili oluşturun.  
  
4.  İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.  
  
5.  Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `service` bağımsız değişken Service.cer adlı bir dosya için hizmet sertifikası computerand dışarı aktarmaları tam etki alanı adı ile bir hizmet sertifikası oluşturur.  
  
6.  Yeni sertifika adını yansıtacak şekilde Service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adıyla aynı olduğu. Ayrıca bilgisayar adını değiştirmek \<hizmet > /\<baseAddresses > localhost öğesine hizmet bilgisayarınızın tam adı.  
  
7.  Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.  
  
8.  Bir istemcide çalışmasına `setup.bat client` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya dışarı aktarır.  
  
9. İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin. Localhost sunucunun tam etki alanı adıyla değiştirerek bunu.  
  
10. Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.  
  
11. İstemcide ImportServiceCert.bat yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminde çalıştırın. Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.  
  
12. Sunucusunda, yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminde ImportClientCert.bat çalıştırın. Bu istemci sertifikası LocalMachine - TrustedPeople deposu Client.cer dosyasından alır.  
  
13. Sunucu bilgisayarında, komut istemi penceresinden Service.exe başlatın.  
  
14. İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
1.  Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın. Bu, sunucu ve istemci sertifikaları sertifika deposundan kaldırır.  
  
> [!NOTE]
>  Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="see-also"></a>Ayrıca Bkz.
