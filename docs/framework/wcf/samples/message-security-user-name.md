---
title: İleti Güvenliği Kullanıcı Adı
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 783969342f007895016ed4183257d6b24188d76c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584733"
---
# <a name="message-security-user-name"></a><span data-ttu-id="69696-102">İleti Güvenliği Kullanıcı Adı</span><span class="sxs-lookup"><span data-stu-id="69696-102">Message Security User Name</span></span>
<span data-ttu-id="69696-103">Bu örnek, istemci için Kullanıcı adı kimlik doğrulamasıyla WS-Security kullanan bir uygulamanın nasıl uygulanacağını gösterir ve sunucunun X. 509v3 sertifikasını kullanarak sunucu kimlik doğrulaması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="69696-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="69696-104">İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="69696-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="69696-105">Varsayılan olarak, istemci tarafından sağlanan Kullanıcı adı ve parola geçerli bir Windows hesabında oturum açmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69696-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="69696-106">Bu örnek, [WSHttpBinding](wshttpbinding.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="69696-106">This sample is based on the [WSHttpBinding](wshttpbinding.md).</span></span> <span data-ttu-id="69696-107">Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programından (Client. exe) ve hizmet kitaplığından (Service. dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="69696-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="69696-108">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="69696-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69696-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="69696-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="69696-110">Bu örnekte ayrıca şunları da gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="69696-110">This sample also demonstrates:</span></span>  
  
- <span data-ttu-id="69696-111">Ek yetkilendirmenin gerçekleştirilebileceği şekilde, Windows hesaplarına varsayılan eşleme.</span><span class="sxs-lookup"><span data-stu-id="69696-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
- <span data-ttu-id="69696-112">Hizmet kodundan Arayanın kimlik bilgilerine erişme.</span><span class="sxs-lookup"><span data-stu-id="69696-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="69696-113">Hizmet, Web. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="69696-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="69696-114">Bağlama, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) Varsayılan olarak ileti güvenliğini kullanan bir standart ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="69696-114">The binding is configured with a standard [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="69696-115">Bu örnek, standart [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) istemci Kullanıcı adı kimlik doğrulamasını kullanmak için standardı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="69696-115">This sample sets the standard [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="69696-116">Davranış, hizmet kimlik doğrulaması için Kullanıcı kimlik bilgilerinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="69696-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="69696-117">Sunucu sertifikası, içindeki özniteliğiyle ilgili konu adı için aynı değeri içermelidir `findValue` [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="69696-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
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
</system.serviceModel>  
```  
  
 <span data-ttu-id="69696-118">İstemci uç noktası yapılandırması, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur.</span><span class="sxs-lookup"><span data-stu-id="69696-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="69696-119">İstemci bağlama, uygun ve ile yapılandırılır `securityMode` `authenticationMode` .</span><span class="sxs-lookup"><span data-stu-id="69696-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="69696-120">Bir çapraz bilgisayar senaryosunda çalışırken, hizmet uç noktası adresinin uygun şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="69696-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="69696-121">İstemci uygulama, kullanılacak kullanıcı adını ve parolayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="69696-121">The client implementation sets the user name and password to use.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 <span data-ttu-id="69696-122">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="69696-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="69696-123">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="69696-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="69696-124">MessageSecurity örneklerine eklenen Setup. bat toplu iş dosyası, sertifika tabanlı güvenlik gerektiren bir barındırılan uygulamayı çalıştırmak için sunucuyu ilgili sertifikayla yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="69696-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="69696-125">Toplu iş dosyası iki modda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="69696-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="69696-126">Toplu iş dosyasını tek bilgisayar modunda çalıştırmak için `setup.bat` komut satırına yazın.</span><span class="sxs-lookup"><span data-stu-id="69696-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="69696-127">Hizmet modu türünde çalıştırmak için `setup.bat service` .</span><span class="sxs-lookup"><span data-stu-id="69696-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="69696-128">Bu modu, örneği bilgisayarlar arasında çalıştırırken kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="69696-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="69696-129">Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="69696-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="69696-130">Aşağıdakiler, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="69696-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="69696-131">Sunucu sertifikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="69696-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="69696-132">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69696-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="69696-133">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="69696-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="69696-134">Sertifika, LocalMachine deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="69696-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="69696-135">Setup. bat toplu iş dosyası bir hizmet bağımsız değişkeniyle (gibi) çalışıyorsa% `setup.bat service` SERVER_NAME% bilgisayarın tam etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="69696-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="69696-136">Aksi takdirde, varsayılan olarak localhost olur.</span><span class="sxs-lookup"><span data-stu-id="69696-136">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="69696-137">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme</span><span class="sxs-lookup"><span data-stu-id="69696-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="69696-138">Aşağıdaki satır, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="69696-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="69696-139">Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="69696-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="69696-140">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="69696-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="69696-141">Sertifikanın özel anahtarına izin verme</span><span class="sxs-lookup"><span data-stu-id="69696-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="69696-142">Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, ASP.NET çalışan işlem hesabına erişilebilen LocalMachine deposunda depolanan sunucu sertifikasını yapar.</span><span class="sxs-lookup"><span data-stu-id="69696-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="69696-143">Windows 'un U. S. Ingilizce sürümünü kullanıyorsanız, Setup. bat dosyasını düzenlemeniz ve `NT AUTHORITY\NETWORK SERVICE` hesap adını bölgesel eşdeğerle değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="69696-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="69696-144">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="69696-144">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="69696-145">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="69696-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="69696-146">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="69696-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="69696-147">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="69696-147">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="69696-148">Yolun, MakeCert. exe ve FindPrivateKey. exe ' nin bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="69696-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2. <span data-ttu-id="69696-149">Yönetici ayrıcalıklarıyla açılan bir Geliştirici Komut İstemi Visual Studio için, örnek yükleme klasöründen Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69696-149">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="69696-150">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="69696-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="69696-151">Setup. bat toplu iş dosyası, Visual Studio için Geliştirici Komut İstemi çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="69696-151">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="69696-152">PATH ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="69696-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="69696-153">Bu ortam değişkeni, Visual Studio için bir Geliştirici Komut İstemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="69696-153">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="69696-154">Adresi girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="69696-154">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>
  
4. <span data-ttu-id="69696-155">\Client\bin. adresinden Client. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="69696-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="69696-156">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="69696-156">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="69696-157">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="69696-157">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="69696-158">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="69696-158">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="69696-159">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69696-159">Create a directory on the service computer.</span></span> <span data-ttu-id="69696-160">Internet Information Services yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69696-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2. <span data-ttu-id="69696-161">Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="69696-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="69696-162">Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="69696-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="69696-163">Ayrıca Setup. bat ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="69696-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="69696-164">İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69696-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="69696-165">İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="69696-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="69696-166">Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="69696-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="69696-167">Sunucusunda, `setup.bat service` yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69696-167">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="69696-168">`setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `service` bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="69696-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="69696-169">Web. config dosyasını, bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adını (serviceCertificate öğesinde bulunan findValue özniteliğinde) yansıtacak şekilde düzenleyin`.`</span><span class="sxs-lookup"><span data-stu-id="69696-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7. <span data-ttu-id="69696-170">Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="69696-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="69696-171">İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="69696-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="69696-172">İstemcide, yönetici ayrıcalıklarıyla açılan bir Geliştirici Komut İstemi Visual Studio için ImportServiceCert. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69696-172">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="69696-173">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="69696-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="69696-174">İstemci bilgisayarda, bir komut isteminden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="69696-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="69696-175">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="69696-175">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="69696-176">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="69696-176">To clean up after the sample</span></span>  
  
- <span data-ttu-id="69696-177">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="69696-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="69696-178">Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="69696-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="69696-179">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="69696-179">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="69696-180">Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="69696-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
