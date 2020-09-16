---
title: İleti Güvenliği Anonim
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: 7ba64f28d621dad51957438025de22827405dd87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558673"
---
# <a name="message-security-anonymous"></a><span data-ttu-id="02583-102">İleti Güvenliği Anonim</span><span class="sxs-lookup"><span data-stu-id="02583-102">Message Security Anonymous</span></span>
<span data-ttu-id="02583-103">Ileti güvenliği anonim örneği, istemci kimlik doğrulaması olmadan ileti düzeyinde güvenlik kullanan ancak sunucunun X. 509.440 sertifikasını kullanarak sunucu kimlik doğrulaması gerektiren bir Windows Communication Foundation (WCF) uygulamasının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="02583-103">The Message Security Anonymous sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="02583-104">İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="02583-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="02583-105">Bu örnek, [WSHttpBinding](wshttpbinding.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="02583-105">This sample is based on the [WSHttpBinding](wshttpbinding.md) sample.</span></span> <span data-ttu-id="02583-106">Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programından (. exe) ve hizmet kitaplığından (. dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="02583-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="02583-107">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="02583-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="02583-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="02583-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="02583-109">Bu örnek, `True` istemci kimlik doğrulamasından geçirilmediğinden döndüren Hesaplayıcı arabirimine yeni bir işlem ekler.</span><span class="sxs-lookup"><span data-stu-id="02583-109">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>

```csharp
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

 <span data-ttu-id="02583-110">Hizmet, bir yapılandırma dosyası (Web.config) kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="02583-110">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="02583-111">Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="02583-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="02583-112">Bağlama bir bağlama ile yapılandırılır `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="02583-112">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="02583-113">Bağlama için varsayılan güvenlik modu `wsHttpBinding` `Message` .</span><span class="sxs-lookup"><span data-stu-id="02583-113">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="02583-114">`clientCredentialType`Özniteliği olarak ayarlanır `None` .</span><span class="sxs-lookup"><span data-stu-id="02583-114">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

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

 <span data-ttu-id="02583-115">Hizmet kimlik doğrulaması için kullanılacak kimlik bilgileri içinde belirtilir [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="02583-115">The credentials to be used for service authentication are specified in the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="02583-116">Sunucu sertifikası, `SubjectName` `findValue` Aşağıdaki örnek kodda gösterildiği gibi, özniteliği için belirtilen değer olarak aynı değeri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="02583-116">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>

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

 <span data-ttu-id="02583-117">İstemci uç noktası yapılandırması, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur.</span><span class="sxs-lookup"><span data-stu-id="02583-117">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="02583-118">Bağlama için istemci güvenlik modu `wsHttpBinding` `Message` .</span><span class="sxs-lookup"><span data-stu-id="02583-118">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="02583-119">`clientCredentialType`Özniteliği olarak ayarlanır `None` .</span><span class="sxs-lookup"><span data-stu-id="02583-119">The `clientCredentialType` attribute is set to `None`.</span></span>

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

 <span data-ttu-id="02583-120">Örnek, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> hizmet sertifikasının kimliğini doğrulamak için öğesini olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="02583-120">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="02583-121">Bu, bölümünde istemcinin App.config dosyasında yapılır `behaviors` .</span><span class="sxs-lookup"><span data-stu-id="02583-121">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="02583-122">Bu, sertifika kullanıcının güvenilir kişiler depoluiyorsa, sertifikanın veren zincirinin doğrulanması yapılmadan güvenilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="02583-122">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="02583-123">Bu ayar, örneğin bir sertifika yetkilisi (CA) tarafından verilen sertifikalara gerek kalmadan çalıştırılabilmesi için kolaylık sağlamak amacıyla burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02583-123">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="02583-124">Bu ayar varsayılan, ChainTrust değerinden daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="02583-124">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="02583-125">Bu ayarın güvenlik etkileri, üretim kodunda kullanılmadan önce dikkatle düşünülmelidir `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="02583-125">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>

 <span data-ttu-id="02583-126">İstemci uygulama yöntemine bir çağrı ekler ve bu `IsCallerAnonymous` nedenle [WSHttpBinding](wshttpbinding.md) örneğinden farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="02583-126">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](wshttpbinding.md) sample.</span></span>

```csharp
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

 <span data-ttu-id="02583-127">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="02583-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="02583-128">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="02583-128">Press ENTER in the client window to shut down the client.</span></span>

```console
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="02583-129">Ileti güvenliği anonim örneğine eklenen Setup.bat toplu iş dosyası, sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikayla yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="02583-129">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="02583-130">Toplu iş dosyası iki modda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="02583-130">The batch file can be run in two modes.</span></span> <span data-ttu-id="02583-131">Toplu iş dosyasını tek bilgisayar modunda çalıştırmak için `setup.bat` komut satırına yazın.</span><span class="sxs-lookup"><span data-stu-id="02583-131">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="02583-132">Hizmet modunda çalıştırmak için yazın `setup.bat service` .</span><span class="sxs-lookup"><span data-stu-id="02583-132">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="02583-133">Örneği bilgisayarlar arasında çalıştırırken bu modu kullanın.</span><span class="sxs-lookup"><span data-stu-id="02583-133">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="02583-134">Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="02583-134">See the setup procedure at the end of this topic for details.</span></span>

 <span data-ttu-id="02583-135">Aşağıdakiler, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="02583-135">The following provides a brief overview of the different sections of the batch files:</span></span>

- <span data-ttu-id="02583-136">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="02583-136">Creating the server certificate.</span></span>

     <span data-ttu-id="02583-137">Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="02583-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="02583-138">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="02583-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="02583-139">Sertifika, LocalMachine deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="02583-139">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="02583-140">Kurulum Batch dosyası bir hizmet bağımsız değişkeniyle (örneğin `setup.bat service` ,) çalışıyorsa% SERVER_NAME% bilgisayarın tam etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="02583-140">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="02583-141">Aksi takdirde, varsayılan olarak localhost olur.</span><span class="sxs-lookup"><span data-stu-id="02583-141">Otherwise it defaults to localhost.</span></span>

- <span data-ttu-id="02583-142">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="02583-142">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="02583-143">Aşağıdaki satır, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="02583-143">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="02583-144">Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="02583-144">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="02583-145">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="02583-145">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="02583-146">Sertifikanın özel anahtarına izin veriliyor.</span><span class="sxs-lookup"><span data-stu-id="02583-146">Granting permissions on the certificate's private key.</span></span>

     <span data-ttu-id="02583-147">Setup.bat Batch dosyasındaki aşağıdaki satırlar, LocalMachine deposunda depolanan sunucu sertifikasını ASP.NET çalışan işlem hesabına erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="02583-147">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> <span data-ttu-id="02583-148">U-U olmayan bir. S kullanıyorsanız. Windows 'un İngilizce sürümü Setup.bat dosyasını düzenlemeniz ve `NT AUTHORITY\NETWORK SERVICE` hesap adını bölgesel eşdeğerle değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="02583-148">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="02583-149">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="02583-149">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="02583-150">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="02583-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="02583-151">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="02583-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="02583-152">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="02583-152">To run the sample on the same computer</span></span>

1. <span data-ttu-id="02583-153">Yolun Makecert.exe ve FindPrivateKey.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="02583-153">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>

2. <span data-ttu-id="02583-154">Visual Studio için Geliştirici Komut İstemi örnek install klasöründen yönetici ayrıcalıklarıyla Çalıştır ' a Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="02583-154">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="02583-155">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="02583-155">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="02583-156">Kurulum toplu iş dosyası, Visual Studio için bir Geliştirici Komut İstemi çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="02583-156">The setup batch file is designed to be run from a  Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="02583-157">PATH ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="02583-157">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="02583-158">Bu ortam değişkeni, Visual Studio için bir Geliştirici Komut İstemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="02583-158">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="02583-159">Adresi girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="02583-159">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
4. <span data-ttu-id="02583-160">\Client\bin. 'den başlatma Client.exe</span><span class="sxs-lookup"><span data-stu-id="02583-160">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="02583-161">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="02583-161">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="02583-162">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="02583-162">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="02583-163">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="02583-163">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="02583-164">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="02583-164">Create a directory on the service computer.</span></span> <span data-ttu-id="02583-165">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="02583-165">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="02583-166">Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="02583-166">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="02583-167">Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="02583-167">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="02583-168">Ayrıca, Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="02583-168">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="02583-169">İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="02583-169">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="02583-170">İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="02583-170">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="02583-171">Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="02583-171">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="02583-172">Sunucusunda, `setup.bat service` yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="02583-172">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="02583-173">`setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `service` bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="02583-173">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="02583-174">Web.config, `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adını (içindeki özniteliğinde) yansıtacak şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="02583-174">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="02583-175">Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="02583-175">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="02583-176">İstemci bilgisayardaki Client.exe.config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="02583-176">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="02583-177">İstemcisinde ImportServiceCert.bat, yönetici ayrıcalıklarıyla açılmış bir Visual Studio Geliştirici Komut İstemi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="02583-177">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="02583-178">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="02583-178">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="02583-179">İstemci bilgisayarda, bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="02583-179">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="02583-180">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="02583-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="02583-181">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="02583-181">To clean up after the sample</span></span>  
  
- <span data-ttu-id="02583-182">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="02583-182">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02583-183">Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="02583-183">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="02583-184">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="02583-184">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="02583-185">Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="02583-185">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>
