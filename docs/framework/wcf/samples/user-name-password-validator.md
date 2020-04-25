---
title: Kullanıcı AdıParola Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: e66188cfe1874c4d4097f3f842fd19cfdd4c79f1
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141272"
---
# <a name="user-name-password-validator"></a><span data-ttu-id="28535-102">Kullanıcı AdıParola Doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="28535-102">User Name Password Validator</span></span>
<span data-ttu-id="28535-103">Bu örnek, nasıl özel bir UserNamePassword doğrulayıcısı uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28535-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="28535-104">Bu, yerleşik UserNamePassword doğrulama modlarından hiçbirinin uygulamanın gereksinimlerine uygun olmadığı durumlarda faydalıdır; Örneğin, Kullanıcı adı/parola çiftleri bir veritabanı gibi bazı dış depoda depolanır.</span><span class="sxs-lookup"><span data-stu-id="28535-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="28535-105">Bu örnek, iki belirli Kullanıcı adı/parola çiftini denetleyen özel bir doğrulayıcısı olan bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="28535-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="28535-106">İstemci, hizmette kimlik doğrulamak için böyle bir Kullanıcı adı/parola çifti kullanır.</span><span class="sxs-lookup"><span data-stu-id="28535-106">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="28535-107">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="28535-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="28535-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="28535-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="28535-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (wcf) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="28535-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28535-110">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="28535-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> <span data-ttu-id="28535-111">Herkes özel Doğrulayıcının kabul ettiği Kullanıcı adı/parola çiftlerini kullanan bir Kullanıcı adı kimlik bilgisi oluşturabileceğinden, hizmet standart UserNamePassword doğrulayıcısı tarafından sunulan varsayılan davranıştan daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="28535-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="28535-112">Standart UserNamePassword Doğrulayıcısı, belirtilen Kullanıcı adı/parola çiftini bir Windows hesabıyla eşlemeye çalışır ve bu eşleme başarısız olursa kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="28535-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="28535-113">Bu örnekteki özel UserNamePassword doğrulayıcısı üretim kodunda kullanılmamalıdır, yalnızca çizim amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="28535-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="28535-114">Özet bölümünde bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="28535-114">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="28535-115">İstemcinin kimliği, bir Kullanıcı adı belirteci kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="28535-115">The client can be authenticated using a Username Token.</span></span>

- <span data-ttu-id="28535-116">Sunucu, istemci kimlik bilgilerini özel bir Usernamepassworddoğrulayıcısı ile doğrular ve özel hataları Kullanıcı adı ve parola doğrulama mantığındaki istemciye nasıl yayılır.</span><span class="sxs-lookup"><span data-stu-id="28535-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

- <span data-ttu-id="28535-117">Sunucunun sunucu X. 509.440 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="28535-117">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="28535-118">Hizmet, App. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="28535-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="28535-119">Bağlama, varsayılan olarak WS-güvenlik `wsHttpBinding` ve Kullanıcı adı kimlik doğrulamasını kullanan bir standart ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="28535-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Security and username authentication.</span></span> <span data-ttu-id="28535-120">Hizmet davranışı, istemci kullanıcı `Custom` adı/parola çiftlerini Doğrulayıcı sınıfının türüyle birlikte doğrulama modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="28535-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="28535-121">Davranışı, `serviceCertificate` öğesini kullanarak sunucu sertifikasını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="28535-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="28535-122">Sunucu sertifikasının, `SubjectName` [ \<ServiceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)için `findValue` aynı değeri içermesi vardır.</span><span class="sxs-lookup"><span data-stu-id="28535-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

 <span data-ttu-id="28535-123">İstemci uç noktası yapılandırması, bir yapılandırma adından, hizmet uç noktası için mutlak bir adresten, bağlamaya ve sözleşmeyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="28535-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="28535-124">İstemci bağlama uygun mod ve iletiyle `clientCredentialType`yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="28535-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="28535-125">İstemci uygulama kullanıcıdan bir Kullanıcı adı ve parola girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="28535-125">The client implementation prompts the user to enter a username and password.</span></span>

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

 <span data-ttu-id="28535-126">Bu örnek, Kullanıcı adı/parola çiftlerini doğrulamak için özel bir UserNamePasswordValidator kullanır.</span><span class="sxs-lookup"><span data-stu-id="28535-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="28535-127">Örnek `CustomUserNamePasswordValidator`, öğesinden <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>türetilir.</span><span class="sxs-lookup"><span data-stu-id="28535-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="28535-128">Daha fazla bilgi <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> için belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="28535-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="28535-129">Bu özel Doğrulayıcı örneği, `Validate` aşağıdaki kodda gösterildiği gibi iki belirli Kullanıcı adı/parola çiftini kabul etmek için yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="28535-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

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

 <span data-ttu-id="28535-130">Doğrulayıcı hizmet koduna uygulandıktan sonra, hizmet ana bilgisayarının kullanılacak Doğrulayıcı örneği hakkında bilgilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="28535-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="28535-131">Bu, aşağıdaki kod kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="28535-131">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="28535-132">Ya da yapılandırma ile aynı şeyi aşağıdaki şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28535-132">Or you can do the same thing in configuration as follows.</span></span>

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
   </serviceCredentials>
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="28535-133">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="28535-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="28535-134">İstemci tüm yöntemleri başarıyla çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28535-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="28535-135">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="28535-135">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="28535-136">Toplu Iş dosyası kurulumu</span><span class="sxs-lookup"><span data-stu-id="28535-136">Setup Batch File</span></span>
 <span data-ttu-id="28535-137">Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="28535-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="28535-138">Bu toplu iş dosyası makineler arasında çalışacak şekilde değiştirilmelidir veya şirket içinde olmayan bir durumda çalışır.</span><span class="sxs-lookup"><span data-stu-id="28535-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="28535-139">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="28535-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="28535-140">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="28535-140">Creating the server certificate:</span></span>

     <span data-ttu-id="28535-141">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28535-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="28535-142">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="28535-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="28535-143">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="28535-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="28535-144">Varsayılan değer localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="28535-144">The default value is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="28535-145">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="28535-145">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="28535-146">Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="28535-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="28535-147">Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="28535-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="28535-148">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="28535-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="28535-149">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="28535-149">To set up and build the sample</span></span>

1. <span data-ttu-id="28535-150">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="28535-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="28535-151">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="28535-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="28535-152">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="28535-152">To run the sample on the same machine</span></span>

1. <span data-ttu-id="28535-153">Visual Studio 2012 komut istemi içindeki örnek yükleme klasöründen Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="28535-153">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="28535-154">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="28535-154">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="28535-155">Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="28535-155">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="28535-156">Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="28535-156">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="28535-157">Service\bin. adresinden Service. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="28535-157">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="28535-158">\Client\bin. adresinden Client. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="28535-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="28535-159">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="28535-159">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="28535-160">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="28535-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="28535-161">Örneği makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="28535-161">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="28535-162">Hizmet ikili dosyaları için hizmet makinesinde bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="28535-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="28535-163">Hizmet programı dosyalarını hizmet makinesindeki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="28535-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="28535-164">Ayrıca Setup. bat ve Cleanup. bat dosyalarını hizmet makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="28535-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="28535-165">Makinenin tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="28535-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="28535-166">Sunucu yapılandırma dosyasının bu yeni sertifika adını yansıtması için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="28535-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="28535-167">Sunucu sertifikasını istemcinin CurrentUser-Trustedkişilerim deposuna kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="28535-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="28535-168">Bunu yalnızca, sunucu sertifikası güvenilen bir veren tarafından verilmiyorsa yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="28535-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="28535-169">Hizmet makinesindeki App. config dosyasında, temel adresin değerini localhost yerine tam nitelikli bir makine adı belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="28535-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="28535-170">Hizmet makinesinde, bir komut istemi penceresinden Service. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="28535-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="28535-171">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="28535-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="28535-172">İstemci makinesindeki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="28535-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="28535-173">İstemci makinesinde, bir komut istemi penceresinden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="28535-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="28535-174">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="28535-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="28535-175">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="28535-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="28535-176">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="28535-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="28535-177">Bu, sunucu sertifikasını sertifika deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="28535-177">This removes the server certificate from the certificate store.</span></span>  
