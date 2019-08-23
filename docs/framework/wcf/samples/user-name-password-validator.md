---
title: Kullanıcı AdıParola Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: b02533641785b24019f10a3c224b09e252cbb2ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966779"
---
# <a name="user-name-password-validator"></a>Kullanıcı AdıParola Doğrulayıcı
Bu örnek, nasıl özel bir UserNamePassword doğrulayıcısı uygulanacağını gösterir. Bu, yerleşik UserNamePassword doğrulama modlarından hiçbirinin uygulamanın gereksinimlerine uygun olmadığı durumlarda faydalıdır; Örneğin, Kullanıcı adı/parola çiftleri bir veritabanı gibi bazı dış depoda depolanır. Bu örnek, iki belirli Kullanıcı adı/parola çiftini denetleyen özel bir doğrulayıcısı olan bir hizmeti gösterir. İstemci, hizmette kimlik doğrulamak için böyle bir Kullanıcı adı/parola çifti kullanır.

> [!IMPORTANT]
>  Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> Herkes özel Doğrulayıcının kabul ettiği Kullanıcı adı/parola çiftlerini kullanan bir Kullanıcı adı kimlik bilgisi oluşturabileceğinden, hizmet standart UserNamePassword doğrulayıcısı tarafından sunulan varsayılan davranıştan daha az güvenlidir. Standart UserNamePassword Doğrulayıcısı, belirtilen Kullanıcı adı/parola çiftini bir Windows hesabıyla eşlemeye çalışır ve bu eşleme başarısız olursa kimlik doğrulaması başarısız olur. Bu örnekteki özel UserNamePassword doğrulayıcısı üretim kodunda kullanılmamalıdır, yalnızca çizim amaçlıdır.

 Özet bölümünde bu örnek şunları gösterir:

- İstemcinin kimliği, bir Kullanıcı adı belirteci kullanılarak yapılabilir.

- Sunucu, istemci kimlik bilgilerini özel bir Usernamepassworddoğrulayıcısı ile doğrular ve özel hataları Kullanıcı adı ve parola doğrulama mantığındaki istemciye nasıl yayılır.

- Sunucunun sunucu X. 509.440 sertifikası kullanılarak kimlik doğrulaması yapılır.

 Hizmet, App. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bağlama, varsayılan olarak WS-güvenlik `wsHttpBinding` ve Kullanıcı adı kimlik doğrulamasını kullanan bir standart ile yapılandırılır. Hizmet davranışı, istemci kullanıcı `Custom` adı/parola çiftlerini Doğrulayıcı sınıfının türüyle birlikte doğrulama modunu belirtir. Davranışı, `serviceCertificate` öğesini kullanarak sunucu sertifikasını da belirtir. Sunucu sertifikasının, `SubjectName` `findValue` [ServiceCertificate > için aynı \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)değeri içermesi vardır.

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <!-- use host/baseAddresses to configure base address provided by host -->
      <host>
        <baseAddresses>
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />
        </baseAddresses>
      </host>
      <!-- use base address specified above, provide one endpoint -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- username binding -->
      <binding name="Binding">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceDebug includeExceptionDetailInFaults ="true"/>
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to
          specify a custom validator for username/password
          combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom"
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

 İstemci uç noktası yapılandırması, bir yapılandırma adından, hizmet uç noktası için mutlak bir adresten, bağlamaya ve sözleşmeyle oluşur. İstemci bağlama uygun mod ve iletiyle `clientCredentialType`yapılandırılır.

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
address="http://localhost:8001/servicemodelsamples/service/username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
```

 İstemci uygulama kullanıcıdan bir Kullanıcı adı ve parola girmesini ister.

```
// Get the username and password
Console.WriteLine("Username authentication required.");
Console.WriteLine("Provide a username.");
Console.WriteLine("   Enter username: (test1)");
string username = Console.ReadLine();
Console.WriteLine("   Enter password:");
string password = "";
ConsoleKeyInfo info = Console.ReadKey(true);
while (info.Key != ConsoleKey.Enter)
{
    if (info.Key != ConsoleKey.Backspace)
    {
        if (info.KeyChar != '\0')
        {
            password += info.KeyChar;
        }
        info = Console.ReadKey(true);
    }
    else if (info.Key == ConsoleKey.Backspace)
    {
        if (password != "")
        {
            password = password.Substring(0, password.Length - 1);
        }
        info = Console.ReadKey(true);
    }
}
for (int i = 0; i < password.Length; i++)
{
    Console.Write("*");
}
Console.WriteLine();
// Create a proxy with Certificate endpoint configuration
CalculatorProxy proxy = new CalculatorProxy("Username")
try
{
  proxy.ClientCredentials.Username.Username = username;
  proxy.ClientCredentials.Username.Password = password;
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = proxy.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
  }
  catch (Exception e)
  {
      Console.WriteLine("Call failed:");
      while (e != null)
      {
          Console.WriteLine("\t{0}", e.Message);
          e = e.InnerException;
      }
      proxy.Abort();
  }
}
```

 Bu örnek, Kullanıcı adı/parola çiftlerini doğrulamak için özel bir UserNamePasswordValidator kullanır. Örnek `CustomUserNamePasswordValidator`, öğesinden <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>türetilir. Daha fazla bilgi <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> için belgelerine bakın. Bu özel Doğrulayıcı örneği, `Validate` aşağıdaki kodda gösterildiği gibi iki belirli Kullanıcı adı/parola çiftini kabul etmek için yöntemini uygular.

```
public class CustomUserNameValidator : UserNamePasswordValidator
{
 // This method validates users. It allows in two users,
 // test1 and test2 with passwords 1tset and 2tset respectively.
 // This code is for illustration purposes only and
 // MUST NOT be used in a production environment because it
 // is NOT secure.
 public override void Validate(string userName, string password)
 {
  if (null == userName || null == password)
  {
   throw new ArgumentNullException();
  }

  if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
  {
   throw new FaultException("Unknown Username or Incorrect Password");
   }
  }
 }
```

 Doğrulayıcı hizmet koduna uygulandıktan sonra, hizmet ana bilgisayarının kullanılacak Doğrulayıcı örneği hakkında bilgilendirilmesi gerekir. Bu, aşağıdaki kod kullanılarak yapılır.

```
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 Ya da yapılandırma ile aynı şeyi aşağıdaki şekilde yapabilirsiniz.

```xml
<behaviors>
 <serviceBehaviors>
  <behavior name="CalculatorServiceBehavior">
  ...
   <serviceCredentials>
    <!--
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.
    -->
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemci tüm yöntemleri başarıyla çağırmalıdır. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Toplu Iş dosyası kurulumu
 Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır. Bu toplu iş dosyası makineler arasında çalışacak şekilde değiştirilmelidir veya şirket içinde olmayan bir durumda çalışır.

 Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.

- Sunucu sertifikası oluşturuluyor:

     Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. % SERVER_NAME% değişkeni sunucu adını belirtiyor. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Varsayılan değer localhost 'tur.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme:

     Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve derlemek için

1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.

2. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.

#### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için

1. Visual Studio 2012 komut istemi içindeki örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    >  Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.  
  
2. Service\bin. adresinden Service. exe ' yi Başlat  
  
3. \Client\bin. adresinden Client. exe ' yi Başlat İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-machines"></a>Örneği makineler arasında çalıştırmak için  
  
1. Hizmet ikili dosyaları için hizmet makinesinde bir dizin oluşturun.  
  
2. Hizmet programı dosyalarını hizmet makinesindeki hizmet dizinine kopyalayın. Ayrıca Setup. bat ve Cleanup. bat dosyalarını hizmet makinesine kopyalayın.  
  
3. Makinenin tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına ihtiyacınız vardır. Sunucu yapılandırma dosyasının bu yeni sertifika adını yansıtması için güncelleştirilmeleri gerekir.  
  
4. Sunucu sertifikasını istemcinin CurrentUser-Trustedkişilerim deposuna kopyalayın. Bunu yalnızca, sunucu sertifikası güvenilen bir veren tarafından verilmiyorsa yapmanız gerekir.  
  
5. Hizmet makinesindeki App. config dosyasında, temel adresin değerini localhost yerine tam nitelikli bir makine adı belirtecek şekilde değiştirin.  
  
6. Hizmet makinesinde, bir komut istemi penceresinden Service. exe ' yi başlatın.  
  
7. İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci makinesine kopyalayın.  
  
8. İstemci makinesindeki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.  
  
9. İstemci makinesinde, bir komut istemi penceresinden Client. exe ' yi başlatın.  
  
10. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
1. Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın. Bu, sunucu sertifikasını sertifika deposundan kaldırır.  
