---
title: "İleti Güvenliği Anonim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
caps.latest.revision: "52"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 561e451656cd725a732ea727badeb47087252b9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="message-security-anonymous"></a><span data-ttu-id="16af0-102">İleti Güvenliği Anonim</span><span class="sxs-lookup"><span data-stu-id="16af0-102">Message Security Anonymous</span></span>
<span data-ttu-id="16af0-103">İleti güvenliği anonim örnek nasıl uygulandığını gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ileti düzeyi güvenlik herhangi bir istemci kimlik doğrulaması kullanan ancak sunucunun X.509 sertifikası kullanılarak kimlik doğrulaması gerektiren uygulama.</span><span class="sxs-lookup"><span data-stu-id="16af0-103">The Message Security Anonymous sample demonstrates how to implement a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="16af0-104">İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="16af0-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="16af0-105">Bu örnek dayanır [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="16af0-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span> <span data-ttu-id="16af0-106">Bu örnek, bir istemci konsol program (.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="16af0-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="16af0-107">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="16af0-107">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16af0-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="16af0-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="16af0-109">Bu örnek yeni bir işlem döndürür hesaplayıcı arabirimi ekler `True` istemci doğrulanmadı durumunda.</span><span class="sxs-lookup"><span data-stu-id="16af0-109">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>  
  
```  
public class CalculatorService : ICalculator  
{  
    public bool IsCallerAnonymous()  
    {  
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.  
        return ServiceSecurityContext.Current.IsAnonymous;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="16af0-110">Hizmet yapılandırma dosyasında (Web.config) kullanılarak tanımlanmış hizmet ile iletişim için tek bir uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="16af0-110">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="16af0-111">Uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="16af0-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="16af0-112">Bağlama ile yapılandırılmış bir `wsHttpBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="16af0-112">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="16af0-113">Varsayılan güvenlik modunu `wsHttpBinding` bağlama `Message`.</span><span class="sxs-lookup"><span data-stu-id="16af0-113">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="16af0-114">`clientCredentialType` Özniteliği `None`.</span><span class="sxs-lookup"><span data-stu-id="16af0-114">The `clientCredentialType` attribute is set to `None`.</span></span>  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
     <!--   
     <!--This configuration defines the security mode as Message and-->  
     <!--the clientCredentialType as None. This mode provides -- >  
     <!--server authentication only using the service certificate.-->  
  
     <binding>  
       <security mode="Message">  
         <message clientCredentialType="None" />  
       </security>  
     </binding>  
    </wsHttpBinding>  
  </bindings>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="16af0-115">Hizmet kimlik doğrulaması için kullanılacak kimlik bilgileri belirtilen [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span><span class="sxs-lookup"><span data-stu-id="16af0-115">The credentials to be used for service authentication are specified in the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="16af0-116">Sunucu sertifikası için aynı değeri içermelidir `SubjectName` için belirtilen değer olarak `findValue` özniteliği aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="16af0-116">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>  
      <!--   
    The serviceCredentials behavior allows you to define a service certificate.  
    A service certificate is used by a client to authenticate the service and provide message protection.  
    This configuration references the "localhost" certificate installed during the setup instructions.  
    -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
      </serviceCredentials>  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="16af0-117">Hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="16af0-117">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="16af0-118">İstemci güvenlik modunu `wsHttpBinding` bağlama `Message`.</span><span class="sxs-lookup"><span data-stu-id="16af0-118">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="16af0-119">`clientCredentialType` Özniteliği `None`.</span><span class="sxs-lookup"><span data-stu-id="16af0-119">The `clientCredentialType` attribute is set to `None`.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
             address="http://localhost/servicemodelsamples/service.svc"   
             binding="wsHttpBinding"   
             behaviorConfiguration="ClientCredentialsBehavior"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--This configuration defines the security mode as -->  
      <!--Message and the clientCredentialType as None. -->  
      <binding name="Binding1">  
        <security mode = "Message">  
          <message clientCredentialType="None"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>   
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="16af0-120">Örnek kümeleri <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> için <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> hizmetin sertifika kimlik doğrulaması için.</span><span class="sxs-lookup"><span data-stu-id="16af0-120">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="16af0-121">Bu istemcinin App.config dosyasında yapılır `behaviors` bölümü.</span><span class="sxs-lookup"><span data-stu-id="16af0-121">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="16af0-122">Bu sertifika kullanıcının güvenilir kişiler deposunda ise, daha sonra sertifikanın veren zinciri doğrulamasının yapmadan güvenilir olduğunu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="16af0-122">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="16af0-123">Örnek bir sertifika yetkilisi (CA) tarafından verilen sertifikalara gerek kalmadan çalışabilmesi bu ayarı buraya kolaylık sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16af0-123">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="16af0-124">Bu ayar ChainTrust varsayılan daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="16af0-124">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="16af0-125">Bu ayar güvenlik etkilerini kullanmadan önce dikkatle düşünülmelidir `PeerOrChainTrust` üretim kodunda.</span><span class="sxs-lookup"><span data-stu-id="16af0-125">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>  
  
 <span data-ttu-id="16af0-126">İstemci uygulaması için bir çağrı ekler `IsCallerAnonymous` yöntemi ve aksi durumda farklı değil [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="16af0-126">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  
  
```  
// Create a client with a client endpoint configuration.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity operation.  
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());  
  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
...  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="16af0-127">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="16af0-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="16af0-128">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="16af0-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
IsCallerAnonymous returned: True  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="16af0-129">İleti güvenliği anonim örnekle dahil Setup.bat toplu iş dosyası, sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için uygun bir sertifika sunucusunu yapılandırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="16af0-129">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="16af0-130">Toplu iş dosyası iki modda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16af0-130">The batch file can be run in two modes.</span></span> <span data-ttu-id="16af0-131">Tek bilgisayar modunda toplu iş dosyasını çalıştırmak için şunu yazın `setup.bat` komut satırında.</span><span class="sxs-lookup"><span data-stu-id="16af0-131">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="16af0-132">Bu hizmet modunda çalıştırmak için yazın `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="16af0-132">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="16af0-133">Bu mod, örnek bilgisayarlar arasında çalıştırırken kullanın.</span><span class="sxs-lookup"><span data-stu-id="16af0-133">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="16af0-134">Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="16af0-134">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="16af0-135">Toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="16af0-135">The following provides a brief overview of the different sections of the batch files:</span></span>  
  
-   <span data-ttu-id="16af0-136">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="16af0-136">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="16af0-137">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16af0-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="16af0-138">% Sunucu_adı % değişkeni sunucusunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="16af0-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="16af0-139">Sertifika saklanır LocalMachine deposundaki.</span><span class="sxs-lookup"><span data-stu-id="16af0-139">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="16af0-140">Kurulum toplu iş dosyası hizmetinin bağımsız değişkenlerle çalıştırırsanız (gibi `setup.bat service`) sunucu_adı % bilgisayarın tam etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="16af0-140">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="16af0-141">Aksi takdirde localhost için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="16af0-141">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="16af0-142">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="16af0-142">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="16af0-143">Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="16af0-143">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="16af0-144">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="16af0-144">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="16af0-145">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="16af0-145">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="16af0-146">Sertifikanın özel anahtarı izin verme.</span><span class="sxs-lookup"><span data-stu-id="16af0-146">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="16af0-147">Erişilebilir LocalMachine deposundaki depolanan sunucu sertifikası Setup.bat toplu iş dosyası aşağıdaki satırları olun [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] çalışan işlem hesabı.</span><span class="sxs-lookup"><span data-stu-id="16af0-147">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
    ```  
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="16af0-148">ABD dışındaki kullanıyorsanız Setup.bat dosyasını düzenleyin ve yerini Windows İngilizce sürümünü `NT AUTHORITY\NETWORK SERVICE` bölgesel eşdeğer. hesap adı.</span><span class="sxs-lookup"><span data-stu-id="16af0-148">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="16af0-149">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="16af0-149">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="16af0-150">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16af0-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="16af0-151">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16af0-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="16af0-152">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="16af0-152">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="16af0-153">Yolun Makecert.exe ve FindPrivateKey.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="16af0-153">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2.  <span data-ttu-id="16af0-154">Visual Studio komut istemini yönetici ayrıcalıklarıyla çalıştırın örnek yükleme klasöründeki Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="16af0-154">Run Setup.bat from the sample install folder in a Visual Studio command prompt run with administrator privileges.</span></span> <span data-ttu-id="16af0-155">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="16af0-155">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="16af0-156">Kurulum toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]komut istemi.</span><span class="sxs-lookup"><span data-stu-id="16af0-156">The setup batch file is designed to be run from a  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]Command Prompt.</span></span> <span data-ttu-id="16af0-157">Path ortam değişkeni SDK yüklendiği dizinine işaret etmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="16af0-157">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="16af0-158">Bu ortam değişkenini içinde otomatik olarak ayarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]komut istemi.</span><span class="sxs-lookup"><span data-stu-id="16af0-158">This environment variable is automatically set within a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]Command Prompt.</span></span>  
  
3.  <span data-ttu-id="16af0-159">Adres http://localhost/servicemodelsamples/service.svc girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="16af0-159">Verify access to the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
4.  <span data-ttu-id="16af0-160">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="16af0-160">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="16af0-161">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="16af0-161">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="16af0-162">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="16af0-162">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="16af0-163">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="16af0-163">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="16af0-164">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16af0-164">Create a directory on the service computer.</span></span> <span data-ttu-id="16af0-165">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16af0-165">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="16af0-166">Hizmet program dosyalarını \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="16af0-166">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="16af0-167">\Bin alt dizinindeki dosyaları kopyalayın emin olun.</span><span class="sxs-lookup"><span data-stu-id="16af0-167">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="16af0-168">Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="16af0-168">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="16af0-169">İstemci ikili dosyalarının için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16af0-169">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="16af0-170">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="16af0-170">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="16af0-171">Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="16af0-171">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="16af0-172">Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="16af0-172">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="16af0-173">Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="16af0-173">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="16af0-174">Web.config dosyasını yeni sertifika yansıtacak şekilde düzenleyin (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), bilgisayarın tam etki alanı adı ile aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="16af0-174">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="16af0-175">Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="16af0-175">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="16af0-176">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="16af0-176">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="16af0-177">İstemci üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="16af0-177">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="16af0-178">Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="16af0-178">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="16af0-179">İstemci bilgisayarda bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="16af0-179">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="16af0-180">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="16af0-180">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="16af0-181">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="16af0-181">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="16af0-182">Örnek çalıştıran bitirdikten sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="16af0-182">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16af0-183">Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="16af0-183">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="16af0-184">Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun.</span><span class="sxs-lookup"><span data-stu-id="16af0-184">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="16af0-185">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="16af0-185">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16af0-186">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16af0-186">See Also</span></span>
