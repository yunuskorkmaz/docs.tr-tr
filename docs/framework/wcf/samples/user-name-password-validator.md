---
title: Kullanıcı AdıParola Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 4ad365061e6a0f3178650699febd6c18cdd14205
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553125"
---
# <a name="user-name-password-validator"></a><span data-ttu-id="46630-102">Kullanıcı AdıParola Doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="46630-102">User Name Password Validator</span></span>
<span data-ttu-id="46630-103">Bu örnek, nasıl özel bir UserNamePassword doğrulayıcısı uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="46630-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="46630-104">Bu, yerleşik UserNamePassword doğrulama modlarından hiçbirinin uygulamanın gereksinimlerine uygun olmadığı durumlarda faydalıdır; Örneğin, Kullanıcı adı/parola çiftleri bir veritabanı gibi bazı dış depoda depolanır.</span><span class="sxs-lookup"><span data-stu-id="46630-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="46630-105">Bu örnek, iki belirli Kullanıcı adı/parola çiftini denetleyen özel bir doğrulayıcısı olan bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="46630-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="46630-106">İstemci, hizmette kimlik doğrulamak için böyle bir Kullanıcı adı/parola çifti kullanır.</span><span class="sxs-lookup"><span data-stu-id="46630-106">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="46630-107">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="46630-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="46630-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="46630-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="46630-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="46630-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46630-110">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="46630-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> <span data-ttu-id="46630-111">Herkes özel Doğrulayıcının kabul ettiği Kullanıcı adı/parola çiftlerini kullanan bir Kullanıcı adı kimlik bilgisi oluşturabileceğinden, hizmet standart UserNamePassword doğrulayıcısı tarafından sunulan varsayılan davranıştan daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="46630-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="46630-112">Standart UserNamePassword Doğrulayıcısı, belirtilen Kullanıcı adı/parola çiftini bir Windows hesabıyla eşlemeye çalışır ve bu eşleme başarısız olursa kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="46630-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="46630-113">Bu örnekteki özel UserNamePassword doğrulayıcısı üretim kodunda kullanılmamalıdır, yalnızca çizim amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="46630-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="46630-114">Özet bölümünde bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="46630-114">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="46630-115">İstemcinin kimliği, bir Kullanıcı adı belirteci kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="46630-115">The client can be authenticated using a Username Token.</span></span>

- <span data-ttu-id="46630-116">Sunucu, istemci kimlik bilgilerini özel bir Usernamepassworddoğrulayıcısı ile doğrular ve özel hataları Kullanıcı adı ve parola doğrulama mantığındaki istemciye nasıl yayılır.</span><span class="sxs-lookup"><span data-stu-id="46630-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

- <span data-ttu-id="46630-117">Sunucunun sunucu X. 509.440 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="46630-117">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="46630-118">Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="46630-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="46630-119">Bağlama, `wsHttpBinding` Varsayılan olarak WS-güvenlik ve Kullanıcı adı kimlik doğrulamasını kullanan bir standart ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="46630-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Security and username authentication.</span></span> <span data-ttu-id="46630-120">Hizmet davranışı, `Custom` istemci Kullanıcı adı/parola çiftlerini Doğrulayıcı sınıfının türüyle birlikte doğrulama modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="46630-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="46630-121">Davranışı, öğesini kullanarak sunucu sertifikasını da belirtir `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="46630-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="46630-122">Sunucu sertifikasının, içindeki ile için aynı değeri içermesi vardır `SubjectName` `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="46630-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

 <span data-ttu-id="46630-123">İstemci uç noktası yapılandırması, bir yapılandırma adından, hizmet uç noktası için mutlak bir adresten, bağlamaya ve sözleşmeyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="46630-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="46630-124">İstemci bağlama uygun mod ve iletiyle yapılandırılır `clientCredentialType` .</span><span class="sxs-lookup"><span data-stu-id="46630-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="46630-125">İstemci uygulama kullanıcıdan bir Kullanıcı adı ve parola girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="46630-125">The client implementation prompts the user to enter a username and password.</span></span>

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

 <span data-ttu-id="46630-126">Bu örnek, Kullanıcı adı/parola çiftlerini doğrulamak için özel bir UserNamePasswordValidator kullanır.</span><span class="sxs-lookup"><span data-stu-id="46630-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="46630-127">Örnek `CustomUserNamePasswordValidator` , öğesinden türetilir <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> .</span><span class="sxs-lookup"><span data-stu-id="46630-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="46630-128"><xref:System.IdentityModel.Selectors.UserNamePasswordValidator>Daha fazla bilgi için belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="46630-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="46630-129">Bu özel Doğrulayıcı örneği, `Validate` aşağıdaki kodda gösterildiği gibi iki belirli Kullanıcı adı/parola çiftini kabul etmek için yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="46630-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

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

 <span data-ttu-id="46630-130">Doğrulayıcı hizmet koduna uygulandıktan sonra, hizmet ana bilgisayarının kullanılacak Doğrulayıcı örneği hakkında bilgilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="46630-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="46630-131">Bu, aşağıdaki kod kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="46630-131">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="46630-132">Ya da yapılandırma ile aynı şeyi aşağıdaki şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46630-132">Or you can do the same thing in configuration as follows.</span></span>

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

 <span data-ttu-id="46630-133">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="46630-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="46630-134">İstemci tüm yöntemleri başarıyla çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46630-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="46630-135">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="46630-135">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="46630-136">Toplu Iş dosyası kurulumu</span><span class="sxs-lookup"><span data-stu-id="46630-136">Setup Batch File</span></span>
 <span data-ttu-id="46630-137">Bu örneğe eklenen Setup.bat Batch dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="46630-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="46630-138">Bu toplu iş dosyası makineler arasında çalışacak şekilde değiştirilmelidir veya şirket içinde olmayan bir durumda çalışır.</span><span class="sxs-lookup"><span data-stu-id="46630-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="46630-139">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="46630-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="46630-140">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="46630-140">Creating the server certificate:</span></span>

     <span data-ttu-id="46630-141">Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46630-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="46630-142">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="46630-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="46630-143">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="46630-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="46630-144">Varsayılan değer localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="46630-144">The default value is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="46630-145">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="46630-145">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="46630-146">Setup.bat Batch dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="46630-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="46630-147">Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="46630-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="46630-148">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="46630-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="46630-149">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="46630-149">To set up and build the sample</span></span>

1. <span data-ttu-id="46630-150">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="46630-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="46630-151">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="46630-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="46630-152">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="46630-152">To run the sample on the same machine</span></span>

1. <span data-ttu-id="46630-153">Visual Studio 2012 komut istemi içindeki örnek install klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="46630-153">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="46630-154">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="46630-154">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="46630-155">Setup.bat Batch dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="46630-155">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="46630-156">Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni, Setup.bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="46630-156">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="46630-157">Service\bin. 'den başlatma Service.exe</span><span class="sxs-lookup"><span data-stu-id="46630-157">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="46630-158">\Client\bin. 'den başlatma Client.exe</span><span class="sxs-lookup"><span data-stu-id="46630-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="46630-159">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="46630-159">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="46630-160">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="46630-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="46630-161">Örneği makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="46630-161">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="46630-162">Hizmet ikili dosyaları için hizmet makinesinde bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="46630-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="46630-163">Hizmet programı dosyalarını hizmet makinesindeki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="46630-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="46630-164">Ayrıca, Setup.bat ve Cleanup.bat dosyalarını hizmet makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="46630-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="46630-165">Makinenin tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="46630-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="46630-166">Sunucu yapılandırma dosyasının bu yeni sertifika adını yansıtması için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="46630-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="46630-167">Sunucu sertifikasını istemcinin CurrentUser-Trustedkişilerim deposuna kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="46630-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="46630-168">Bunu yalnızca, sunucu sertifikası güvenilen bir veren tarafından verilmiyorsa yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46630-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="46630-169">Hizmet makinesindeki App.config dosyasında, temel adresin değerini localhost yerine tam nitelikli bir makine adı belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="46630-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="46630-170">Hizmet makinesinde, bir komut istemi penceresinden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="46630-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="46630-171">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="46630-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="46630-172">İstemci makinesindeki Client.exe.config dosyasında, bitiş noktasının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="46630-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="46630-173">İstemci makinesinde, bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="46630-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="46630-174">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="46630-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="46630-175">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="46630-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="46630-176">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="46630-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="46630-177">Bu, sunucu sertifikasını sertifika deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="46630-177">This removes the server certificate from the certificate store.</span></span>
