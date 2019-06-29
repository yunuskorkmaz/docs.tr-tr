---
title: Kullanıcı AdıParola Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 16e5f854dbe76150945145c0ce81d0d5fa4ac0d0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421820"
---
# <a name="user-name-password-validator"></a>Kullanıcı AdıParola Doğrulayıcı
Bu örnek bir özel UserNamePassword Doğrulayıcıyı uygulamak nasıl gösterir. Bu, yerleşik UserNamePassword doğrulama modları hiçbiri uygulama gereksinimlerini için uygun olduğu durumlarda kullanışlıdır. Örneğin, ne zaman kullanıcı adı/parola çiftleri bir veritabanı gibi bazı dış deposunda depolanır. Bu örnek için iki belirli bir kullanıcı adı/parola çiftleri denetleyen özel Doğrulayıcı sağlayıcısı olan bir hizmete gösterir. İstemci hizmete kimlik doğrulaması için bu tür bir kullanıcı adı/parola çift kullanır.

> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
>  Herkes özel Doğrulayıcı kabul eden kullanıcı adı/parola çiftleri kullanan bir kullanıcı adı kimlik bilgisi oluşturmak için standart UserNamePassword doğrulayıcı tarafından sağlanan varsayılan davranışını daha az güvenli bir hizmettir. Standart UserNamePassword Doğrulayıcı sağlanan kullanıcı adı/parola çifti için bir Windows hesabı eşlemeye çalışır ve bu Eşleme başarısız kimlik doğrulaması başarısız olur. Bu örnekte UserNamePassword Doğrulayıcı üretim kodunda kullanılmamalıdır özel, buna yalnızca gösterim amacıyla var.

 Özet olarak, bu örnek gösterir nasıl:

- İstemci, bir kullanıcı adı belirteci kullanılarak doğrulanabilir.

- Sunucu, istemci kimlik bilgileri bir özel usernamepasswordvalidator değerini ve istemciye kullanıcı adını ve parolayı Doğrulama mantığı özel hata yaymak nasıl karşı doğrular.

- Sunucu sunucusunun X.509 sertifikasını kullanarak kimlik doğrulaması yapılır.

 Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar. Uç nokta, adres, bağlama ve bir sözleşme oluşur. Bir standart yapılandırılmış bağlama `wsHttpBinding` , varsayılan olarak WS-güvenlik ve kullanıcı adı kimlik doğrulaması için kullanılacak. Hizmet davranışı belirtir `Custom` doğrulamak için istemci kullanıcı adı/parola çiftleri Doğrulayıcı sınıfını türünü birlikte modu. Sunucu sertifikası kullanarak davranışı da belirtir `serviceCertificate` öğesi. Sunucu sertifikası için aynı değeri içermesi gerekir `SubjectName` olarak `findValue` içinde [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

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

 İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin bir yapılandırma adı oluşur. Bağlama istemcinin uygun modu ve şu iletiyle yapılandırıldığı `clientCredentialType`.

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

 İstemci uygulaması, bir kullanıcı adı ve parola girmesini ister.

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

 Bu örnek, kullanıcı adı/parola çiftlerini doğrulamak için özel bir usernamepasswordvalidator değerini kullanır. Örnek uygulayan `CustomUserNamePasswordValidator`, türetilmiş <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Belgelerine bakın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> daha fazla bilgi için. Bu belirli özel Doğrulayıcı sağlayıcısı örnek uygulayan `Validate` aşağıdaki kodda gösterildiği gibi iki belirli bir kullanıcı adı/parola çiftlerini kabul etmek için yöntemi.

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

 Doğrulayıcı hizmeti kodunda uygulandıktan sonra hizmet ana bilgisayarı kullanmak için Doğrulayıcı örneği hakkında bilgilendirilmesi gerekir. Bu yapılır aşağıdaki kodu kullanarak.

```
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 Ya da aynı şeyi yapılandırmasında şu şekilde yapabilirsiniz.

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

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci başarıyla tüm yöntemlerini çağırmanız gerekir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Kurulum toplu iş dosyası
 Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası makinelerde çalışmaya veya kendi kendine barındırılan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.

- Sunucu sertifikası oluşturuluyor:

     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun. % Sunucu_adı % değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Localhost varsayılan değerdir.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor:

     İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için

1. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için aşağıdaki yönergeleri kullanın.

#### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için

1. Setup.bat içinde bir Visual Studio 2012 komut istemi örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.

    > [!NOTE]
    >  Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır. PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın.  
  
2. Service.exe service\bin ' başlatın.  
  
3. Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-machines"></a>Makineler arasında örneği çalıştırmak için  
  
1. Hizmet makinede hizmet ikili dosyaları için bir dizin oluşturun.  
  
2. Hizmet program dosyaları hizmeti makinede hizmet dizine kopyalayın. Ayrıca hizmeti makineye Setup.bat ve Cleanup.bat dosyaları kopyalayın.  
  
3. Makinenin tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası gerekir. Sunucu Yapılandırma dosyası, bu yeni sertifika adı yansıtacak şekilde güncelleştirilmesi gerekir.  
  
4. Sunucu sertifikasını istemcinin CurrentUser TrustedPeople depoya kopyalayın. Yalnızca sunucu sertifikası güvenilir bir veren tarafından yazılmazsa yapmanız gerekir.  
  
5. Hizmeti makinede App.config dosyasında taban adresi localhost yerine tam makine adını değiştirin.  
  
6. Bir komut istemi penceresinden Service.exe hizmeti makinede başlatın.  
  
7. İstemci program dosyaları \client\bin\ klasöründen, dile özgü klasörünün altındaki istemci makineye kopyalayın.  
  
8. İstemci makinesinde Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.  
  
9. İstemci makinesinde bir komut istemi penceresinden Client.exe başlatın.  
  
10. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
1. Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın. Bu sunucu sertifikası sertifika deposundan kaldırır.  
