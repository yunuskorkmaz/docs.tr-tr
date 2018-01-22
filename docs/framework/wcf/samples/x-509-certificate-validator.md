---
title: "X.509 Sertifika Doğrulayıcı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08ccbbf50db089841d2af2205c7a7cb289a8767c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="x509-certificate-validator"></a>X.509 Sertifika Doğrulayıcı
Bu örnek, özel bir X.509 Sertifika Doğrulayıcı uygulama gösterilmiştir. Bu, yerleşik X.509 Sertifika doğrulama modları hiçbiri uygulama gereksinimleri için uygun olduğu durumlarda yararlıdır. Bu örnekte kendi kendine verilen sertifikaların kabul özel bir doğrulayıcı sahip bir hizmeti gösterilmektedir. İstemci, bir hizmetin kimliğini bu tür bir sertifika kullanır.  
  
 Not: herhangi bir kendi kendine sertifikayı oluşturabileceğiniz gibi hizmeti tarafından kullanılan özel Doğrulayıcı ChainTrust X509CertificateValidationMode tarafından sağlanan varsayılan davranışı daha az güvenlidir. Bu güvenlik uygulamalarını, üretim kodunda bu doğrulama mantığını kullanmadan önce dikkatle düşünülmelidir.  
  
 Bu örnek özetinde gösterir nasıl:  
  
-   İstemci, bir X.509 sertifikası kullanılarak doğrulanabilir.  
  
-   Sunucu, istemci kimlik bilgileri özel X509CertificateValidator karşı doğrular.  
  
-   Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanır.  
  
 Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için tek bir uç noktasını kullanıma sunar. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur. Bağlama ile standart bir yapılandırılmış `wsHttpBinding` , varsayılan olarak kullanmaya `WSSecurity` ve istemci sertifikası kimlik doğrulaması. Hizmet davranışı Doğrulayıcı sınıfını türü ile birlikte istemci X.509 sertifikalarını doğrularken için özel modunu belirtir. Davranış da serviceCertificate öğesi kullanarak sunucu sertifikası belirtir. Sunucu sertifikası için aynı değeri içermesi gerekir `SubjectName` olarak `findValue` içinde [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).  
  
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
            <!--The serviceCredentials behavior allows one -->  
            <!-- to specify authentication constraints on -->  
            <!-- client certificates. -->  
            <clientCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- Custom means that if the custom -->  
              <!-- X509CertificateValidator does NOT throw -->  
              <!-- an exception, then the provided certificate -- >  
              <!-- will be trusted without performing any -->  
              <!-- validation beyond that performed by the custom-->  
              <!-- validator. The security implications of this -->  
              <!-- setting should be carefully considered before -->  
              <!-- using Custom in production code. -->  
              <authentication   
                 certificateValidationMode="Custom"   
                 customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />  
            </clientCertificate>  
            <!-- The serviceCredentials behavior allows one to -- >  
            <!--define a service certificate. -->  
            <!--A service certificate is used by a client to  -->  
            <!--authenticate the service and provide message  -->  
            <!--protection. This configuration references the  -->  
            <!--"localhost" certificate installed during the setup  -->  
            <!--instructions. -->  
            <serviceCertificate findValue="localhost"   
                 storeLocation="LocalMachine"   
                 storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
      </system.serviceModel>  
```  
  
 Yapılandırma adı, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur. Bağlama istemcinin uygun modunu ve ileti yapılandırıldığı `clientCredentialType`.  
  
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
  
 İstemci uygulaması istemci sertifikası kullanacak şekilde ayarlar.  
  
```  
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
  
 Bu örnek özel X509CertificateValidator sertifikalarını doğrulamak için kullanır. Örnek türetilmiş CustomX509CertificateValidator uygulayan <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Belgelerine bakın <xref:System.IdentityModel.Selectors.X509CertificateValidator> daha fazla bilgi için. Bu belirli özel Doğrulayıcı örnek aşağıdaki kodda gösterildiği gibi kendi kendine verilen herhangi bir X.509 sertifikayı kabul etmek için Doğrula yöntemini uygular.  
  
```  
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
  
 Doğrulayıcı hizmet kodunda tamamlandıktan sonra hizmet ana bilgisayarı kullanmak için Doğrulayıcı örneği hakkında bilgi sahibi olmak gerekir. Bu yapılır aşağıdaki kodu kullanarak.  
  
```  
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 Veya yapılandırma aynı şeyi şu şekilde yapabilirsiniz.  
  
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
    <!--throw an exception, then the provided certificate will-- >   
    <!-- be trusted without performing any validation beyond that-- >  
    <!-- performed by the custom validator. The security -- >   
    <!--implications of this setting should be carefully -- >  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci, başarıyla tüm yöntemleri çağırmanız gerekir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
## <a name="setup-batch-file"></a>Toplu iş dosyası Kurulumu  
 Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:  
  
-   Sunucu sertifikası oluşturuluyor:  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun. % Sunucu_adı % değişkeni sunucusunun adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Localhost varsayılan değerdir.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme:  
  
     İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar. MakeCert.exe tarafından oluşturulan sertifikaları istemci sistem tarafından dolaylı olarak güvenilmeyen olduğundan bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   İstemci sertifikası oluşturma:  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak istemci sertifikası oluşturun. % USER_NAME % değişkeni istemci adını belirtir. Bu istemci kodu arar adı olduğu için bu değer "test1" ayarlanır. USER_NAME % değerini değiştirirseniz Client.cs kaynak dosyası içinde karşılık gelen değerle değiştirin ve istemci yeniden oluşturun.  
  
     Sertifika Currentuser'a depolama konumu altında (Kişisel) My deposunda saklanır.  
  
    ```  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   İstemci sertifikası sunucunun güvenilen sertifika deposuna yükleme:  
  
     Setup.bat toplu iş dosyası aşağıdaki satırları istemci sertifikası güvenilir Kişiler deposuna kopyalayın. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak sunucu sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir güvenilen kök sertifika kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — istemci sertifikası ile sunucu sertifika depolama doldurma, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Bir tek - veya çapraz-computerconfiguration içinde örneği çalıştırmak için aşağıdaki yönergeleri kullanın.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  İçinde örnek yükleme klasöründen Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla açılır. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!IMPORTANT]
    >  Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi. İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.  
  
2.  Service.exe service\bin başlatın.  
  
3.  Launch Client.exe from \client\bin. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda bir dizin oluşturun.  
  
2.  Hizmet program dosyalarını \service\bin hizmeti bilgisayarında sanal dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat, GetComputerName.vbs ve ImportClientCert.bat dosyaları hizmet bilgisayara kopyalayın.  
  
3.  Bir dizin üzerinde istemci computerfor istemci ikili dosyalarının oluşturun.  
  
4.  İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.  
  
5.  Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `service` bağımsız değişkeni computerand dışarı tam etki alanı adı ile bir hizmet sertifikası Service.cer adlı bir dosyaya hizmet sertifikası oluşturur.  
  
6.  Yeni sertifika yansıtacak şekilde Service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adı ile aynı olduğu. Ayrıca bilgisayar adını değiştirme \<hizmet > /\<baseAddresses > localhost öğesine hizmet bilgisayarınızı tam adı.  
  
7.  Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.  
  
8.  İstemci üzerinde çalışan `setup.bat client` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.  
  
9. İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin. Sunucunun tam etki alanı adı ile localhost değiştirerek bunu.  
  
10. Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.  
  
11. İstemci üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.  
  
12. Sunucu üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportClientCert.bat çalıştırın. Bu istemci sertifikası LocalMachine - TrustedPeople deposunda Client.cer dosyadan alır.  
  
13. Sunucu bilgisayarda komut istemi penceresinden Service.exe başlatın.  
  
14. İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
1.  Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın. Bu sunucu ve istemci sertifikaları sertifika deposundan kaldırır.  
  
> [!NOTE]
>  Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Ayrıca Bkz.
