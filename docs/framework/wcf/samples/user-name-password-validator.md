---
title: "Kullanıcı AdıParola Doğrulayıcı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 07083d7a92f6b4de68cd1d618d57291f64bef0fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="user-name-password-validator"></a><span data-ttu-id="ffbbe-102">Kullanıcı AdıParola Doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="ffbbe-102">User Name Password Validator</span></span>
<span data-ttu-id="ffbbe-103">Bu örnek, bir özel UserNamePassword Doğrulayıcıyı uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="ffbbe-104">Bu, yerleşik UserNamePassword doğrulama modları hiçbiri uygulama gereksinimleri için uygun olduğu durumlarda kullanışlıdır. Örneğin, ne zaman kullanıcı adı/parola çiftleri bir veritabanı gibi bazı dış deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="ffbbe-105">Bu örnek için iki belirli kullanıcı adı/parola çiftleri denetler özel bir doğrulayıcı sahip bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="ffbbe-106">İstemci bu tür bir kullanıcı adı/parola çifti hizmetin kimliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-106">The client uses such a username/password pair to authenticate to the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ffbbe-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ffbbe-108">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ffbbe-109">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ffbbe-110">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
>  <span data-ttu-id="ffbbe-111">Herkes özel Doğrulayıcı kabul kullanıcı adı/parola çiftleri kullanan bir kullanıcı adı kimlik bilgisi oluşturmak için standart UserNamePassword Doğrulayıcısı tarafından sağlanan varsayılan davranışı daha az güvenli bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="ffbbe-112">Standart UserNamePassword Doğrulayıcı sağlanan kullanıcı adı/parola çifti Windows hesabına eşlemeye çalışır ve bu Eşleme başarısız kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="ffbbe-113">Bu örnekte UserNamePassword Doğrulayıcı üretim kodunda kullanılmamalıdır özel, bu yalnızca gösterim amacıyla gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>  
  
 <span data-ttu-id="ffbbe-114">Bu örnek özetinde gösterir nasıl:</span><span class="sxs-lookup"><span data-stu-id="ffbbe-114">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="ffbbe-115">İstemci, bir kullanıcı adı belirteci kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-115">The client can be authenticated using a Username Token.</span></span>  
  
-   <span data-ttu-id="ffbbe-116">Sunucu, istemci kimlik bilgileri özel usernamepasswordvalidator değerini ve kullanıcı adı ve parola doğrulama mantığını gelen özel hatalarının istemciye yaymak nasıl karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>  
  
-   <span data-ttu-id="ffbbe-117">Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-117">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="ffbbe-118">Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için tek bir uç noktasını kullanıma sunar. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="ffbbe-119">Bağlama ile standart bir yapılandırılmış `wsHttpBinding` , varsayılan olarak WS-güvenlik ve kullanıcı adı kimlik doğrulaması için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Securityand username authentication.</span></span> <span data-ttu-id="ffbbe-120">Hizmet davranışını belirtir `Custom` Doğrulayıcı sınıfını türü ile birlikte istemci kullanıcı adı/parola çiftleri doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="ffbbe-121">Sunucu sertifikası kullanarak davranışı da belirtir `serviceCertificate` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="ffbbe-122">Sunucu sertifikası için aynı değeri içermesi gerekir `SubjectName` olarak `findValue` içinde [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="ffbbe-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="ffbbe-123">Yapılandırma adı, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="ffbbe-124">Bağlama istemcinin uygun modunu ve ileti yapılandırıldığı `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
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
  
 <span data-ttu-id="ffbbe-125">İstemci uygulama kullanıcının bir kullanıcı adı ve parola girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-125">The client implementation prompts the user to enter a username and password.</span></span>  
  
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
  
 <span data-ttu-id="ffbbe-126">Bu örnek, kullanıcı adı/parola çiftlerini doğrulamak için özel bir usernamepasswordvalidator değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="ffbbe-127">Örnek uygulayan `CustomUserNamePasswordValidator`, türetilmiş <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="ffbbe-128">Belgelerine bakın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="ffbbe-129">Bu belirli özel Doğrulayıcı örnek uygulayan `Validate` aşağıdaki kodda gösterildiği gibi iki belirli kullanıcı adı/parola çiftlerini kabul yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="ffbbe-130">Doğrulayıcı hizmet kodunda tamamlandıktan sonra hizmet ana bilgisayarı kullanmak için Doğrulayıcı örneği hakkında bilgi sahibi olmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="ffbbe-131">Bu yapılır aşağıdaki kodu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-131">This is done using the following code.</span></span>  
  
```  
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();  
```  
  
 <span data-ttu-id="ffbbe-132">Veya yapılandırma aynı şeyi şu şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-132">Or you can do the same thing in configuration as follows.</span></span>  
  
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
  
 <span data-ttu-id="ffbbe-133">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ffbbe-134">İstemci, başarıyla tüm yöntemleri çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="ffbbe-135">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-135">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="ffbbe-136">Toplu iş dosyası Kurulumu</span><span class="sxs-lookup"><span data-stu-id="ffbbe-136">Setup Batch File</span></span>  
 <span data-ttu-id="ffbbe-137">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="ffbbe-138">Bu toplu iş dosyası makinelerde çalışması için ya da kendi kendine barındırılan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>  
  
 <span data-ttu-id="ffbbe-139">Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="ffbbe-140">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="ffbbe-140">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="ffbbe-141">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="ffbbe-142">% Sunucu_adı % değişkeni sunucusunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="ffbbe-143">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="ffbbe-144">Localhost varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-144">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="ffbbe-145">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="ffbbe-145">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="ffbbe-146">İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ffbbe-147">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ffbbe-148">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="ffbbe-149">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ffbbe-149">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="ffbbe-150">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ffbbe-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="ffbbe-151">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="ffbbe-152">Aynı makinede örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ffbbe-152">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="ffbbe-153">İçinde örnek yükleme klasöründen Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-153">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt.</span></span> <span data-ttu-id="ffbbe-154">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-154">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ffbbe-155">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-155">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="ffbbe-156">İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-156">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="ffbbe-157">Service.exe service\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-157">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="ffbbe-158">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ffbbe-159">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-159">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="ffbbe-160">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ffbbe-160">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="ffbbe-161">Makine genelinde örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ffbbe-161">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="ffbbe-162">Hizmet ikili dosyaları hizmeti makinede bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="ffbbe-163">Hizmet program dosyalarını hizmeti makinede hizmet dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="ffbbe-164">Ayrıca hizmet makineye Setup.bat ve Cleanup.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3.  <span data-ttu-id="ffbbe-165">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="ffbbe-166">Sunucu Yapılandırma dosyası, bu yeni sertifika adını yansıtacak şekilde güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4.  <span data-ttu-id="ffbbe-167">Sunucu sertifikası istemci Currentuser'a TrustedPeople depolama alanına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="ffbbe-168">Yalnızca sunucu sertifikası güvenilir bir veren tarafından verilmemiş varsa bunu yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="ffbbe-169">Hizmeti makinede App.config dosyasında localhost yerine bir makine tam adı belirtmek için taban adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="ffbbe-170">Bir komut istemi penceresinden Service.exe hizmeti makinede başlatın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7.  <span data-ttu-id="ffbbe-171">İstemci makine dile özgü klasörü altındaki \client\bin\ klasöründen istemci program dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8.  <span data-ttu-id="ffbbe-172">İstemci makinesinde Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="ffbbe-173">İstemci makinesinde, bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="ffbbe-174">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ffbbe-174">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ffbbe-175">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="ffbbe-175">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="ffbbe-176">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="ffbbe-177">Bu sunucu sertifikası sertifika deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-177">This removes the server certificate from the certificate store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffbbe-178">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffbbe-178">See Also</span></span>
