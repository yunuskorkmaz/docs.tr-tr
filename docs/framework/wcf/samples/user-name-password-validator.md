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
# <a name="user-name-password-validator"></a><span data-ttu-id="53e17-102">Kullanıcı AdıParola Doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="53e17-102">User Name Password Validator</span></span>
<span data-ttu-id="53e17-103">Bu örnek, özel bir Kullanıcı AdıParola Doğrulayıcısının nasıl uygulanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="53e17-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="53e17-104">Bu, yerleşik UserNamePassword Doğrulama modlarının hiçbirinin uygulama gereksinimleri için uygun olmadığı durumlarda yararlıdır; örneğin, kullanıcı adı/parola çiftleri veritabanı gibi bazı harici depolarda depolandığında.</span><span class="sxs-lookup"><span data-stu-id="53e17-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="53e17-105">Bu örnek, belirli iki kullanıcı adı/parola çiftini denetleyen özel bir doğrulayıcısı olan bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="53e17-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="53e17-106">İstemci, hizmetin kimliğini doğrulamak için böyle bir kullanıcı adı/parola çifti kullanır.</span><span class="sxs-lookup"><span data-stu-id="53e17-106">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53e17-107">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="53e17-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="53e17-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="53e17-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="53e17-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="53e17-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="53e17-110">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="53e17-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> <span data-ttu-id="53e17-111">Herkes, özel doğrulayıcının kabul ettiği kullanıcı adı/parola çiftleri kullanan bir Kullanıcı Adı kimlik bilgisi oluşturabildiği için, hizmet standart UserNamePassword Validator tarafından sağlanan varsayılan davranıştan daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="53e17-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="53e17-112">Standart UserNamePassword Validator, sağlanan kullanıcı adı/parola çiftini bir Windows hesabıyla eşlemeye çalışır ve bu eşleme başarısız olursa kimlik doğrulamayı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="53e17-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="53e17-113">Bu örnekteki özel UserNamePassword Validator üretim kodunda kullanılmamalıdır, sadece illüstrasyon amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="53e17-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="53e17-114">Özetle bu örnek nasıl gösterir:</span><span class="sxs-lookup"><span data-stu-id="53e17-114">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="53e17-115">İstemcinin kimliği kullanıcı adı belirteci kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="53e17-115">The client can be authenticated using a Username Token.</span></span>

- <span data-ttu-id="53e17-116">Sunucu, istemci kimlik bilgilerini özel bir UserNamePasswordValidator'a ve kullanıcı adı ve parola doğrulama mantığından istemciye özel hataların nasıl yayınılayabildiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="53e17-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

- <span data-ttu-id="53e17-117">Sunucu, sunucunun X.509 sertifikası kullanılarak kimlik doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="53e17-117">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="53e17-118">Hizmet, yapılandırma dosyası App.config kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç noktayı ortaya çıkarır. Bitiş noktası bir adres, bir bağlama ve sözleşmeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="53e17-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="53e17-119">Bağlama, varsayılan olarak WS-Security ve kullanıcı adı kimlik doğrulaması kullanmaya varsayılan bir standartla `wsHttpBinding` yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="53e17-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Security and username authentication.</span></span> <span data-ttu-id="53e17-120">Hizmet davranışı, istemci `Custom` adı/parola çiftlerini doğrulama modunu doğrulayıcı sınıfın türüyle birlikte belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e17-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="53e17-121">Davranış ayrıca öğeyi `serviceCertificate` kullanarak sunucu sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e17-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="53e17-122">Sunucu sertifikası, `SubjectName` `findValue` [ \<hizmetSertifikası ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)>'ndekiyle aynı değeri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="53e17-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

 <span data-ttu-id="53e17-123">İstemci bitiş noktası yapılandırması bir yapılandırma adı, hizmet bitiş noktası için mutlak bir adres, bağlama ve sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="53e17-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="53e17-124">İstemci bağlama uygun mod ve `clientCredentialType`ileti ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="53e17-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="53e17-125">İstemci uygulaması, kullanıcıdan bir kullanıcı adı ve parola girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="53e17-125">The client implementation prompts the user to enter a username and password.</span></span>

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

 <span data-ttu-id="53e17-126">Bu örnek, kullanıcı adı/parola çiftleri doğrulamak için özel bir UserNamePasswordValidator kullanır.</span><span class="sxs-lookup"><span data-stu-id="53e17-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="53e17-127">Örnek uygular `CustomUserNamePasswordValidator`, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="53e17-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="53e17-128">Daha fazla <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> bilgi için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="53e17-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="53e17-129">Bu özel doğrulayıcı örnek, `Validate` aşağıdaki kodda gösterildiği gibi iki özel kullanıcı adı/parola çiftini kabul etme yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="53e17-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

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

 <span data-ttu-id="53e17-130">Geçerlilik hizmeti kodunda uygulandıktan sonra, hizmet barındırıcısı kullanılacak geçerlilik örneği hakkında bilgilendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="53e17-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="53e17-131">Bu, aşağıdaki kod kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="53e17-131">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="53e17-132">Ya da aşağıdaki gibi yapılandırma aynı şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53e17-132">Or you can do the same thing in configuration as follows.</span></span>

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

 <span data-ttu-id="53e17-133">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="53e17-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="53e17-134">İstemci tüm yöntemleri başarıyla aramalıdır.</span><span class="sxs-lookup"><span data-stu-id="53e17-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="53e17-135">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="53e17-135">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="53e17-136">Kurulum Toplu Dosya</span><span class="sxs-lookup"><span data-stu-id="53e17-136">Setup Batch File</span></span>
 <span data-ttu-id="53e17-137">Bu örnekte yer alan Setup.bat toplu dosyası, sunucu sertifikası tabanlı güvenlik gerektiren kendi kendine barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="53e17-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="53e17-138">Bu toplu iş dosyası makineler arasında çalışmak veya kendi kendine barındırılmayan bir durumda çalışmak için değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="53e17-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="53e17-139">Aşağıda, uygun yapılandırmada çalışacak şekilde değiştirilebilmeleri için toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="53e17-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="53e17-140">Sunucu sertifikası oluşturma:</span><span class="sxs-lookup"><span data-stu-id="53e17-140">Creating the server certificate:</span></span>

     <span data-ttu-id="53e17-141">Setup.bat toplu dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53e17-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="53e17-142">%SERVER_NAME değişkeni sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e17-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="53e17-143">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="53e17-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="53e17-144">Varsayılan değer yerel ana bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="53e17-144">The default value is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="53e17-145">Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="53e17-145">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="53e17-146">Setup.bat toplu iş dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="53e17-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="53e17-147">Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="53e17-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="53e17-148">Zaten istemci güvenilen bir kök sertifikası köklü bir sertifika varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- sunucu sertifikası ile istemci sertifika deposu doldurma bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="53e17-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="53e17-149">Örneği ayarlamak ve oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="53e17-149">To set up and build the sample</span></span>

1. <span data-ttu-id="53e17-150">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="53e17-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="53e17-151">Numuneyi tek veya makineler arası yapılandırmada çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="53e17-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="53e17-152">Numuneyi aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="53e17-152">To run the sample on the same machine</span></span>

1. <span data-ttu-id="53e17-153">Visual Studio 2012 komut istemi içinde örnek yükleme klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="53e17-153">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="53e17-154">Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="53e17-154">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="53e17-155">Setup.bat toplu dosyası Visual Studio 2012 Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="53e17-155">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="53e17-156">Visual Studio 2012 Komut İstemi içinde ayarlanan PATH ortamı değişkeni, Setup.bat komut dosyasının gerektirdiği yürütülebilir leri içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="53e17-156">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="53e17-157">Service.exe'yi service\bin'den başlatın.</span><span class="sxs-lookup"><span data-stu-id="53e17-157">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="53e17-158">Client.exe'yi \client\bin'den başlatın.</span><span class="sxs-lookup"><span data-stu-id="53e17-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="53e17-159">İstemci etkinliği istemci konsoluygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="53e17-159">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="53e17-160">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="53e17-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="53e17-161">Numuneyi makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="53e17-161">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="53e17-162">Servis ikilileri için servis makinesinde bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="53e17-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="53e17-163">Servis programını servis makinesinde servis dizinini kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="53e17-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="53e17-164">Ayrıca Setup.bat ve Cleanup.bat dosyalarını servis makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="53e17-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="53e17-165">Makinenin tam nitelikli etki alanı adını içeren konu adını içeren bir sunucu sertifikasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="53e17-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="53e17-166">Sunucunun yapılandırma dosyasıbu yeni sertifika adını yansıtacak şekilde güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="53e17-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="53e17-167">Sunucu sertifikasını istemcinin CurrentUser-TrustedPeople deposuna kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="53e17-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="53e17-168">Bunu yalnızca sunucu sertifikası güvenilir bir veren tarafından verilmezse yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="53e17-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="53e17-169">Servis makinesindeki App.config dosyasında, yerel barındırma yerine tam nitelikli bir makine adı belirtmek için temel adresin değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="53e17-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="53e17-170">Servis makinesinde Service.exe komut istemi penceresinden başlatın.</span><span class="sxs-lookup"><span data-stu-id="53e17-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="53e17-171">İstemci programı dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="53e17-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="53e17-172">İstemci makinesindeki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="53e17-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="53e17-173">İstemci makinesinde, istemci.exe komut istemi penceresinden başlatın.</span><span class="sxs-lookup"><span data-stu-id="53e17-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="53e17-174">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="53e17-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="53e17-175">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="53e17-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="53e17-176">Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="53e17-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="53e17-177">Bu, sunucu sertifikasını sertifika deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="53e17-177">This removes the server certificate from the certificate store.</span></span>  
