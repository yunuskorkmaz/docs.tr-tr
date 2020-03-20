---
title: Kullanıcı AdıParola Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 202c7bfc7f60afbad8220950e46c08c0a71eb001
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183245"
---
# <a name="user-name-password-validator"></a>Kullanıcı AdıParola Doğrulayıcı
Bu örnek, özel bir Kullanıcı AdıParola Doğrulayıcısının nasıl uygulanacağını göstermektedir. Bu, yerleşik UserNamePassword Doğrulama modlarının hiçbirinin uygulama gereksinimleri için uygun olmadığı durumlarda yararlıdır; örneğin, kullanıcı adı/parola çiftleri veritabanı gibi bazı harici depolarda depolandığında. Bu örnek, belirli iki kullanıcı adı/parola çiftini denetleyen özel bir doğrulayıcısı olan bir hizmeti gösterir. İstemci, hizmetin kimliğini doğrulamak için böyle bir kullanıcı adı/parola çifti kullanır.

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> Herkes, özel doğrulayıcının kabul ettiği kullanıcı adı/parola çiftleri kullanan bir Kullanıcı Adı kimlik bilgisi oluşturabildiği için, hizmet standart UserNamePassword Validator tarafından sağlanan varsayılan davranıştan daha az güvenlidir. Standart UserNamePassword Validator, sağlanan kullanıcı adı/parola çiftini bir Windows hesabıyla eşlemeye çalışır ve bu eşleme başarısız olursa kimlik doğrulamayı başarısız olur. Bu örnekteki özel UserNamePassword Validator üretim kodunda kullanılmamalıdır, sadece illüstrasyon amaçlıdır.

 Özetle bu örnek nasıl gösterir:

- İstemcinin kimliği kullanıcı adı belirteci kullanılarak doğrulanabilir.

- Sunucu, istemci kimlik bilgilerini özel bir UserNamePasswordValidator'a ve kullanıcı adı ve parola doğrulama mantığından istemciye özel hataların nasıl yayınılayabildiğini doğrular.

- Sunucu, sunucunun X.509 sertifikası kullanılarak kimlik doğrulanır.

 Hizmet, yapılandırma dosyası App.config kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç noktayı ortaya çıkarır. Bitiş noktası bir adres, bir bağlama ve sözleşmeden oluşur. Bağlama, varsayılan olarak WS-Security ve kullanıcı adı kimlik doğrulaması kullanmaya varsayılan bir standartla `wsHttpBinding` yapılandırılır. Hizmet davranışı, istemci `Custom` adı/parola çiftlerini doğrulama modunu doğrulayıcı sınıfın türüyle birlikte belirtir. Davranış ayrıca öğeyi `serviceCertificate` kullanarak sunucu sertifikası belirtir. Sunucu sertifikası, `SubjectName` `findValue` [ \<hizmetSertifikası ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)>'ndekiyle aynı değeri içermelidir.

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

 İstemci bitiş noktası yapılandırması bir yapılandırma adı, hizmet bitiş noktası için mutlak bir adres, bağlama ve sözleşme oluşur. İstemci bağlama uygun mod ve `clientCredentialType`ileti ile yapılandırılır.

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

 İstemci uygulaması, kullanıcıdan bir kullanıcı adı ve parola girmesini ister.

```csharp
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

 Bu örnek, kullanıcı adı/parola çiftleri doğrulamak için özel bir UserNamePasswordValidator kullanır. Örnek uygular `CustomUserNamePasswordValidator`, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>türetilmiştir. Daha fazla <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> bilgi için belgelere bakın. Bu özel doğrulayıcı örnek, `Validate` aşağıdaki kodda gösterildiği gibi iki özel kullanıcı adı/parola çiftini kabul etme yöntemini uygular.

```csharp
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

 Geçerlilik hizmeti kodunda uygulandıktan sonra, hizmet barındırıcısı kullanılacak geçerlilik örneği hakkında bilgilendirilmelidir. Bu, aşağıdaki kod kullanılarak yapılır.

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 Ya da aşağıdaki gibi yapılandırma aynı şeyi yapabilirsiniz.

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

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemci tüm yöntemleri başarıyla aramalıdır. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Kurulum Toplu Dosya
 Bu örnekte yer alan Setup.bat toplu dosyası, sunucu sertifikası tabanlı güvenlik gerektiren kendi kendine barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır. Bu toplu iş dosyası makineler arasında çalışmak veya kendi kendine barındırılmayan bir durumda çalışmak için değiştirilmelidir.

 Aşağıda, uygun yapılandırmada çalışacak şekilde değiştirilebilmeleri için toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlanacaktır.

- Sunucu sertifikası oluşturma:

     Setup.bat toplu dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. %SERVER_NAME değişkeni sunucu adını belirtir. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Varsayılan değer yerel ana bilgisayardır.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme:

     Setup.bat toplu iş dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir. Zaten istemci güvenilen bir kök sertifikası köklü bir sertifika varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- sunucu sertifikası ile istemci sertifika deposu doldurma bu adım gerekli değildir.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve oluşturmak için

1. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.

2. Numuneyi tek veya makineler arası yapılandırmada çalıştırmak için aşağıdaki yönergeleri kullanın.

#### <a name="to-run-the-sample-on-the-same-machine"></a>Numuneyi aynı makinede çalıştırmak için

1. Visual Studio 2012 komut istemi içinde örnek yükleme klasöründen Setup.bat çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.

    > [!NOTE]
    > Setup.bat toplu dosyası Visual Studio 2012 Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 Komut İstemi içinde ayarlanan PATH ortamı değişkeni, Setup.bat komut dosyasının gerektirdiği yürütülebilir leri içeren dizine işaret eder.  
  
2. Service.exe'yi service\bin'den başlatın.  
  
3. Client.exe'yi \client\bin'den başlatın. İstemci etkinliği istemci konsoluygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
#### <a name="to-run-the-sample-across-machines"></a>Numuneyi makineler arasında çalıştırmak için  
  
1. Servis ikilileri için servis makinesinde bir dizin oluşturun.  
  
2. Servis programını servis makinesinde servis dizinini kopyalayın. Ayrıca Setup.bat ve Cleanup.bat dosyalarını servis makinesine kopyalayın.  
  
3. Makinenin tam nitelikli etki alanı adını içeren konu adını içeren bir sunucu sertifikasına ihtiyacınız vardır. Sunucunun yapılandırma dosyasıbu yeni sertifika adını yansıtacak şekilde güncelleştirilmelidir.  
  
4. Sunucu sertifikasını istemcinin CurrentUser-TrustedPeople deposuna kopyalayın. Bunu yalnızca sunucu sertifikası güvenilir bir veren tarafından verilmezse yapmanız gerekir.  
  
5. Servis makinesindeki App.config dosyasında, yerel barındırma yerine tam nitelikli bir makine adı belirtmek için temel adresin değerini değiştirin.  
  
6. Servis makinesinde Service.exe komut istemi penceresinden başlatın.  
  
7. İstemci programı dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci makinesine kopyalayın.  
  
8. İstemci makinesindeki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin.  
  
9. İstemci makinesinde, istemci.exe komut istemi penceresinden başlatın.  
  
10. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
1. Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın. Bu, sunucu sertifikasını sertifika deposundan kaldırır.  
